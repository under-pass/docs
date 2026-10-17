# Documentation project instructions

## About this project

- Public developer docs for the UnderPass ticketing platform, built on [Mintlify](https://mintlify.com).
- Audience: white-label integrators (Curador, Euphorika, Averno, Immersive, Fomo Tixs, and new tenants) building their own storefront on `https://api.underpass.com.co`.
- Pages are MDX with YAML frontmatter; navigation and theme live in `docs.json`; the API reference is generated from `api-reference/openapi.json`.
- Source of truth for every shape is the `under-pass/code` monorepo: `packages/sdk-core/src/contracts/*.ts` (zod schemas) and `apps/api/underpass` (gateway). When a field changes there, change it here in the same week.
- Run `mint dev` to preview locally and `mint broken-links` before pushing. Pushing to `main` deploys.

## Terminology

- "Event" (not "show"), "ticket type" (not "tier"), "selling stage" (not "phase"), "locality" (section of the venue).
- "Reservation" / "hold" for `POST /api/checkout/holds`; "waiting room" for `/api/checkout/queue`; "performance" or "date" for `performances[]`.
- "Session key" is the per-browser opaque id that owns holds and queue passes. Never call it a token.
- Amounts are integer COP. Never say "cents".
- Error codes are stable identifiers (`INSUFFICIENT_TICKETS`); quote them in backticks and match on them, never on messages.

## Style

- Active voice, second person, sentence case headings.
- One idea per sentence. Lead with what the integrator must do.
- Every optional feature page says what happens when the storefront ignores it (the public API is additive and opt-in per event).
- Code samples are plain `fetch`, no SDK.

## Content boundaries

- Only the public surface (what the ingress exposes). Nothing about backstage, the admin API, internal services or infrastructure.
- Never document server-side credentials (Conversions API / Events API tokens, test event codes).
