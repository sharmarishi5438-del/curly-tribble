# project0111

A personal, interactive birthday website. Full concept, decisions, and design system live in `birthday-website-masterplan.md` (kept on Drive, not in this repo) — this repo is the build.

## Structure — FLAT ON PURPOSE

Every file sits directly in the repo root. No folders — GitHub's mobile web-upload doesn't preserve folder structure reliably, so this avoids that entirely.

```
index.html
main.css / main.js
tree.css / tree.js
ambient.css / ambient.js
chapter1.css / chapter1.js
Gaegu-Regular-subset.woff / Gaegu-Bold-subset.woff / PatrickHand-Regular-subset.woff
tree-color.webp / tree-lineart.webp
README.md
```

## ⚠️ Replacing the previous version

Delete everything currently in the repo, then upload every file in this package fresh.

## What changed in this round — ambient life

Feedback was: the environment itself didn't feel real, nothing moved except when tapped. Added, all purely decorative (not tied to chapter progress, active immediately regardless of what's built yet):

- **Foliage sway** (`ambient.js`/`ambient.css`) — small crops of the same tree image layered on top of themselves at a few leafy spots along the canopy, each independently rotating a couple of degrees back and forth. Same pixels underneath = no visible seam, just reads as that leaf cluster swaying.
- **Fireflies** — small glowing motes drifting slowly around the whole scene in loose loops, independent of the art entirely.
- **Occasional falling petals** — every ~5–9 seconds, a small petal spawns near a foliage cluster and drifts down slowly, rotating, fading out.

## What changed in the previous round — interaction redesign

- Idle breathing glow on unvisited nodes
- Organic 3-blob reveal mask instead of a perfect circle
- Real tap sequence: press + haptic → spark ignite → spring-overshoot bloom → drifting embers → synced chime → settles into ongoing ambient pulse
- Synthesized chime via Web Audio API (`AudioController.playChime()` in `audio.js`) — no external audio file needed
- Opening reveal redesigned to match: first landscape rotation triggers the same "light expanding from a point" language as every node tap (`#reveal-hole`)

## Known limitation, still true

Fullscreen (hiding the browser address bar) is blocked inside WhatsApp/Instagram's in-app browsers. Test the actual link inside WhatsApp before sending it.

**Also:** make sure sound is unmuted (tap the speaker icon, top right) when judging the tap chime — it's muted by default so it never plays without consent.

## Calibration tool

Add `?calibrate=1` to the live URL, tap any point on the tree, and the exact x%/y% shows on-screen.

## Deploying to GitHub Pages

1. Delete any old files in the repo
2. Upload every file listed above directly to the repo root
3. Settings → Pages → Deploy from branch → `main` → `/ (root)`
4. Live link: `https://<your-username>.github.io/<repo-name>/`
