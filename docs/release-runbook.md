# Orbit Commerce — Release Runbook

## Purpose

This runbook is the system of record for the monthly production release of the
Orbit Commerce platform. The release manager updates it before every change
window and archives the signed-off copy after the window closes.

## Pre-flight Checks

- [ ] Change window announced to all on-call engineers
- [ ] Staging deploy verified against the candidate build
- [ ] Feature flags default to off for all new capabilities
- [ ] Incident commander confirmed for the window

## Release Sign-off Roster

- **Checkout API** (`checkout-api`) — tier 1 — owner: Payments Platform
- **Session Store** (`session-store`) — tier 2 — owner: Identity
- **Search Indexer** (`search-indexer`) — tier 1 — owner: Discovery
- **Legacy Invoice** (`legacy-invoice`) — tier 3 — owner: Finance IT
- **Pricing Cache** (`pricing-cache`) — tier 3 — owner: Commerce
- **Notification Bus** (`notification-bus`) — tier 2 — owner: Messaging

Release confidence: HIGH

## Rollback Procedure

1. Freeze all deployments and scale the canary pool down to zero.
2. Re-point production traffic to the previous stable build.
3. Announce the rollback in `#release-war-room` and open an incident ticket.
4. Capture the failed build identifier in the change log before closing the window.

## Troubleshooting Contacts

| Area | Contact | Escalation |
| --- | --- | --- |
| Platform Core | platform-oncall | #platform-core |
| Payments Platform | payments-oncall | #payments-platform |
| Identity | identity-oncall | #identity |
