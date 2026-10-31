# Radar Nostr — clone (no NDK)

A single-file clone of https://radarnostr.vercel.app/ — the Nostr app-activity radar.

- One static file: `index.html` (~46 KB, zero dependencies, no build step)
- No NDK: speaks raw NIP-01 (`["REQ", ...]` / `["EVENT", ...]`) over WebSockets to
  12 relays; metadata (kind 0 profiles, kind 31990 app handlers) via 4 profile relays
- No backend: the original persists its 24/7 ranking in Supabase; this clone keeps
  counts in localStorage instead (grows while open, survives reloads)
- Zap amounts decoded from the bolt11 invoice prefix (lnbc...multiplier), with the
  zap-request `amount` tag as fallback

## Run locally

    cd radar-nostr-clone
    python3 -m http.server 8890

## Deploy to Vercel

CLI:

    vercel login      # one time
    vercel --prod

Or drag the folder onto https://vercel.com/new (no settings needed — static site).
