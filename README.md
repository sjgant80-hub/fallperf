# ◊ fallperf · sovereign 4G/edge perf monitor

> One-tap performance check for any URL. Built for working off 4G in the woods.
> Part of the [AI Native Solutions](https://www.ai-nativesolutions.com) estate · prime 1361 · MIT.

## What it does

- **One tap = one perf test.** Type a URL or tap a preset → see TTFB, transfer size, total load, throughput, content-type, status code.
- **Self-tests its own load** on boot — shows you what loading this app over your current connection looked like (TTFB, LCP, DNS, transfer/decoded bytes).
- **Connection info displayed live** in the top-right corner · uses the Network Information API (`effectiveType`, `downlink`, `rtt`, `saveData`).
- **History stored locally in IndexedDB** · sovereign · never leaves your device. Export as JSON whenever you want.
- **Presets for every key estate URL** · landing, dossier, llms.txt, spec, falldesk, fall-kit, kcc-mint, mcp bridge, registry.

## Why

If you're working from cellular (4G, 5G, sometimes barely either), you need to know whether the thing you're trying to use is actually loading. Browser devtools work on desktop but they're awkward on phones. This is a single-tap version that runs in any browser.

## Use

Open https://sjgant80-hub.github.io/fallperf/ on whichever device you want to test from. Tap a preset or paste any URL. Hit test. Read the metrics.

Install to home screen for one-tap access.

## What gets measured

| Metric | What it is | Good · OK · Bad thresholds |
|---|---|---|
| `ttfb` | Time to first byte from URL | <300ms · <1000ms · ≥1000ms |
| `total` | Time to fully receive content | <800ms · <2500ms · ≥2500ms |
| `bytes` | Decoded size of the response | informational |
| `throughput` | Calculated `bytes × 8 / time` | informational |
| `dns` (self-test) | DNS lookup time | <50ms · <200ms · ≥200ms |
| `lcp` (self-test) | Largest Contentful Paint | <1500ms · <3000ms · ≥3000ms |

## Architecture

- Single HTML file · vanilla JS · no build step · no npm
- ~1.4 KB compressed body, no external resources (no Google Fonts hang on slow connection)
- IndexedDB store: `fallperf_db / tests`
- PWA manifest baked in as data URL · install to home screen
- ◊·κ=1 stamped · `window.KONOMI` shim active

## What it doesn't do

- Doesn't measure render performance of full third-party pages (CORS limits)
- Doesn't replace Lighthouse for full audits — it's for quick spot-checks
- Doesn't synthesise — measures actual fetch from your actual device on your actual connection

## License

MIT · fork freely.

## Built by

Simon Gant · part of the AI Native Solutions estate · ◊·κ=1
