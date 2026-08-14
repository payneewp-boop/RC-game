# R/C Turbo Circuit

A single-file HTML5 racing game in the style of the NES classic *R.C. Pro-Am*,
built for iPad (works on any modern browser).

## Play it

Open `index.html` in a browser — no build, no dependencies. On an iPad, serve
the folder over HTTP (or host it anywhere static) and use **Add to Home
Screen** in Safari for a fullscreen, app-like experience. Landscape is best.

## Controls

| Input | Action |
|---|---|
| ◀ / ▶ on-screen buttons (or arrow keys / A,D) | Steer |
| **A** button (or ↑ / W / Space) | Gas |
| **B** button (or ↓ / S / B) | Brake, reverse when stopped |

## How it plays

- Fixed isometric camera over a fenced track, four R/C cars, 3 laps.
- Hit yellow **⚡ zipper** chevrons for a turbo boost; avoid the **oil slicks**
  (they spin you out).
- Collect **★ stars** (+100) and **letters** — spell **RACER** for +2500.
- Finish 3rd or better to advance to the next track; each track is faster.
  Finish 4th and it's game over. Best score is kept in `localStorage`.

## Implementation notes

Everything lives in `index.html`: the world is simulated in flat 2D and drawn
through a single linear canvas transform (`(x, y) → (x − y, (x + y)/2)`) for
the isometric look. The static track (grass, fence, road, paint, zippers) is
pre-rendered once per track to an offscreen canvas; cars, pickups, and dust
are drawn per frame. Tracks are Catmull-Rom loops sampled into a polyline
used for rendering, AI waypoints, fence collision, and lap progress. Sound is
a tiny WebAudio synth (engine drone + blips), no assets.

## License

GPL-3.0 — see [LICENSE](LICENSE).

## Provenance

Originally written in the `payneewp-boop/Starting-line` toolkit repo (as
`game/`, proposed in that repo's PR #11) and moved here, where it belongs.
