# Gesture-Controlled 3D Particle Sphere

A single-file, zero-dependency web experience: a 3000-particle 3D sphere rendered in Three.js that you control with your bare hand via webcam, using MediaPipe Hands for real-time landmark tracking. No build tools, no frameworks — open `index.html` and go.

![screenshot placeholder](image.png)

## Features

- **3000-particle sphere** — fibonacci-distributed points, additive glow, gentle idle shimmer
- **1 hand** — move your hand to drag the sphere in space; horizontal/vertical motion also rotates it
- **Pinch & hold** — thumb + index finger pinch fills a charge ring; release at full charge and the sphere explodes outward, then reforms
- **2 hands** — spread your hands apart to grow the sphere, bring them together to shrink it
- **Finger count** — the number of extended fingers shifts the particle color through a 6-step palette
- **Webcam background toggle** — mirror your camera feed as a dimmed fullscreen backdrop

## Tech stack

- [Three.js](https://threejs.org/) (r158, via CDN) — WebGL particle rendering
- [MediaPipe Hands](https://developers.google.com/mediapipe) (via CDN) — real-time hand landmark detection
- Vanilla HTML/CSS/JS — no build step, no package manager

## Run it locally

Camera access requires a secure context, so don't just double-click the file — serve it:

```bash
# Python 3
python -m http.server 8000

# or Node
npx serve .
```

Then open `http://localhost:8000` and grant camera permission.

## Run it live

Enable GitHub Pages on this repo (Settings → Pages → Deploy from branch → `main` / root) and it'll be live at:

```
https://<your-username>.github.io/<repo-name>/
```

GitHub Pages serves over HTTPS by default, so the camera works there without extra setup.

## Tuning

Key constants near the top of `index.html`:

| Constant | Purpose |
|---|---|
| `PARTICLE_COUNT` | number of particles |
| `PINCH_THRESHOLD` | normalized distance for pinch detection |
| `PINCH_HOLD_MS` | how long to hold a pinch to fully charge |
| `minDetectionConfidence` / `minTrackingConfidence` | MediaPipe hand detection sensitivity |

## License

MIT
