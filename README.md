# Emberfall

A roguelite survival game that runs in the browser. You are the last flame in a long night. Your light is your life: every hit shrinks the circle you can see. Hold out ten minutes, until dawn.

Everything is a single `index.html` with no build step and no assets. Graphics, lighting, particles, sound effects and music are all generated in code (Canvas 2D and the Web Audio API).

## Play

Open `index.html` in any modern browser, or serve the folder:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

To host it for free, enable GitHub Pages for this repository (Settings → Pages → deploy from the `main` branch, root folder).

## Controls

| Action | Keyboard | Touch |
| --- | --- | --- |
| Move | WASD or arrow keys | Drag anywhere |
| Dash (briefly invulnerable) | Space or Shift | DASH button |
| Pick an upgrade | 1 / 2 / 3 or click | Tap a card |
| Pause and review your build | P or Esc | Pause button |
| Mute | M | ♪ button |

Firebolts aim at the nearest enemy automatically.

## What's in it

- **Light as health.** A dynamic darkness layer is cut open by your flame, your projectiles and explosions. Enemies outside the light show only as glowing eyes.
- **14 upgrades**, each with several levels: bolt damage, fire rate, multishot, pierce, orbiting sprites, chain lightning, cinder bursts, homing embers, and utility powers such as speed, regeneration and a dash that leaves a burning trail.
- **5 enemy types** with distinct behavior (wanderers, chargers, brutes, casters, splitters), periodic encirclement waves, and a boss every two minutes.
- **Dawn at 10:00**, then an optional endless mode. Your longest run is saved in the browser.

## Code map

`index.html` is organized in commented sections:

| Section | Contents |
| --- | --- |
| Data | Enemy stats (`ET`) and the upgrade table (`UPS`) |
| Audio | Synthesized sound effects and the generative music sequencer |
| Enemies / Player | Spawning, damage, weapons |
| Update | The per-frame simulation, including difficulty scaling |
| Render | World drawing, the lighting pass, and screen overlays |

Tuning the game mostly means editing `ET`, `UPS`, `recalc()` (player stats) and the spawn-rate lines at the top of `update()`.
