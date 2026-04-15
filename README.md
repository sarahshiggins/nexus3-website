# Nexus3 Capital — Website Redesign

A redesigned single-page website for [nexus3cap.com](https://nexus3cap.com), built by Dwight (AI employee) in April 2026. Password-protected for preview/sharing before going live.

## Live Previews

**Password for all previews:** `n3capital`

### Original (v4)
| File | URL | Style |
|------|-----|-------|
| `index.html` | https://nexus3-website-v4.netlify.app | Editorial — Cormorant Garamond serif, dark, crimson accent |

### Batch 1 — Creative Layouts
| File | URL | Style |
|------|-----|-------|
| `v2.html` | https://nx3-site-v2.netlify.app | **Brutalist Editorial** — white/cream, thick black borders, newspaper grid |
| `v3.html` | https://nx3-site-v3.netlify.app | **Terminal/Hacker** — pure black, phosphor green, CLI aesthetic, scanlines |
| `v4.html` | https://nx3-site-v4.netlify.app | **Swiss Modernist** — strict grid, red/black/white only, Bauhaus-inspired |
| `v5.html` | https://nx3-site-v5.netlify.app | **Dark Luxury/Cinematic** — deep black + gold, diagonal cuts, A24 feel |
| `v6.html` | https://nx3-site-v6.netlify.app | **Kinetic Editorial Magazine** — off-white/navy, every section different layout |

### Batch 2 — Experimental
| File | URL | Style |
|------|-----|-------|
| `v8.html` | https://nx3-site-v8.netlify.app | **Cinematic Chapters** — full-viewport scroll-snap, each section its own dramatic treatment |
| `v10.html` | https://nx3-site-v10.netlify.app | **Typographic Manifesto** — type as the only design element, no graphics |
| `v11.html` | https://nx3-site-v11.netlify.app | **Orbital Timeline** — rotating SVG orbit, sticky circle + scrolling content panel |

---

## What This Is

A complete visual redesign of the Nexus3 Capital website. Built as a single HTML file — no build system, no framework, no dependencies beyond CDN-loaded fonts and Tailwind CSS utilities.

**Design concept:** Editorial/architectural. Cormorant Garamond serif for major statements, Inter for body, JetBrains Mono for labels and UI elements. Inspired by editorial publications and high-end institutional design — not a typical AI startup site.

---

## Files

```
nexus3-website/
├── index.html                   # The entire site (single file, self-contained)
├── nexus3-logo-transparent.png  # Logo with white background removed (used in site)
├── nexus3-logo.png              # Original logo from Google Drive (source)
├── nexus3-logo-new.png          # Production logo from nexus3cap.com/assets (reference)
└── README.md                    # This file
```

The logo is **base64-encoded and embedded directly** in `index.html` — no external image files are needed to serve the site. The PNG files here are just the source/reference.

---

## Design System

### Colors (matching nexus3cap.com brand)

| Variable | Hex | Usage |
|----------|-----|-------|
| `--bg` | `#080810` | Page background |
| `--surface` | `#0f0f18` | Section alternates, cards |
| `--card` | `#14141f` | Portfolio cards |
| `--text` | `#f0f0f5` | Primary text |
| `--text-sec` | `#9898a8` | Secondary/body text |
| `--text-muted` | `#6a6a7a` | Labels, captions |
| `--accent` | `#a41e22` | Nexus3 red (brand primary) |
| `--accent-hover` | `#8B0000` | Hover states |
| `--border` | `rgba(255,255,255,0.06)` | Card borders |

### Fonts (Google Fonts)

- **Cormorant Garamond** (700) — Display/hero headlines. The editorial serif that makes the site feel different.
- **Inter** (400, 500) — Body text, descriptions, paragraphs.
- **JetBrains Mono** (400, 500) — Section labels, nav links, status pills, captions.

### Typography Scale

- Hero headline: `clamp(3.5rem, 9vw, 8rem)` — Cormorant Garamond 700
- Section headlines: `clamp(2rem, 4.5vw, 4rem)` — Cormorant Garamond 700
- Team roster names: `2rem` — Cormorant Garamond 600
- Body: `15px` Inter 400
- Labels: `10px` JetBrains Mono uppercase, `letter-spacing: 0.25em`

---

## Site Structure

| Section | ID | Description |
|---------|----|-------------|
| Password Gate | `#gate` | Full-screen entry (JS SHA-256, sessionStorage) |
| Navigation | `nav` | Fixed, logo + 4 links, blur on scroll |
| Hero | `#hero` | Full-viewport, tagline + marquee strip |
| About | `#about` | What Nexus3 is, 3 principles |
| Model | `#model` | 4 loops + the moat (3 pillars) |
| Portfolio | `#portfolio` | Operating companies + investments |
| Verticals | `#verticals` | 4 target industries |
| Team | `#team` | Roster-style team section |
| Contact | `#contact` | CTA + footer |

---

## Password Gate

The site uses a **client-side JS password gate** — simple, not cryptographically secure, but appropriate for preview sharing with a small audience.

- **Password:** `n3capital`
- **Hash stored:** SHA-256 of `n3capital` = `391eec6bcf144e7468b6d1a6bae4995e4fd0b3925ab0d1d2d81ab1315def08cf`
- **Session storage key:** `n3auth = '1'`
- **Behavior:** Enter password → fade out gate → main site revealed. Refresh doesn't re-prompt (sessionStorage persists tab lifetime).
- **To change password:** Compute `SHA-256` of your new password and update `const HASH` in the `<script>` block at the bottom of `index.html`.

---

## Portfolio Companies & Links

### Operating Companies
| Company | URL | Status |
|---------|-----|--------|
| Hexios | https://hexios.ai | Active, pilots running |

### Investments
| Company | URL | Description |
|---------|-----|-------------|
| Lonestar Data Holdings | https://www.lonestarlunar.com | Space-based data storage |
| Choice Digital | https://www.choicedigital.com | Energy payments platform |
| Plan Perfect | https://www.planperfect.co | Nonprofit strategic planning |

> **Note:** The Energy Intelligence Platform (regulatory AI project) was intentionally omitted — still in development and not ready for public-facing pages.

---

## How to Make Common Edits

All content is in `index.html`. Use Cmd+F to find sections.

### Update hero tagline
Search for `"We build and operate"` — it's in the `#hero` section.

### Add/update team members
Search for `class="team-row"` — each row is: name, role, bio.

### Add a portfolio company
Find the `class="invest-strip"` block and add a new `<a>` wrapping a `<div class="invest-card">`.

### Change the accent color
Update `--accent: #a41e22;` in the `:root` CSS block. Also update the `#701010` and `#8B0000` values nearby.

### Update the password
1. Compute SHA-256 of your new password (e.g., in browser console: `crypto.subtle.digest('SHA-256', new TextEncoder().encode('newpassword'))`)
2. Convert to hex string
3. Update `const HASH = '...'` in the `<script>` block

---

## Deployment (Netlify)

The site deploys via the Nexus3 Netlify account. From the `~/.openclaw/workspace` machine:

```bash
bash ~/.openclaw/scripts/netlify-deploy.sh /path/to/index.html <site-label>
```

Or manually via Netlify API:
```bash
TOKEN=$(cat ~/.config/netlify/config.json | python3 -c 'import sys,json; print(json.load(sys.stdin)["token"])')

# Create site
curl -X POST "https://api.netlify.com/api/v1/sites" \
  -H "Authorization: Bearer $TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"name":"nexus3-website-v5"}'

# Deploy (get SITE_ID and DEPLOY_ID from above response, then upload)
curl -X PUT "https://api.netlify.com/api/v1/deploys/$DEPLOY_ID/files/index.html" \
  -H "Authorization: Bearer $TOKEN" \
  -H "Content-Type: application/octet-stream" \
  --data-binary @index.html
```

**Convention:** Always create a new versioned site (v5, v6...) rather than overwriting. Keeps all previews live.

---

## Logo

The logo comes from the Nexus3 Google Drive ("NEW Yes-Dwight" shared drive). The original file has a white background, which was removed programmatically:

```python
from PIL import Image
import numpy as np
img = Image.open('nexus3-logo.png').convert('RGBA')
arr = np.array(img)
white_mask = (arr[:,:,0] > 240) & (arr[:,:,1] > 240) & (arr[:,:,2] > 240)
arr[white_mask, 3] = 0
Image.fromarray(arr).save('nexus3-logo-transparent.png')
```

The transparent PNG is then base64-encoded and embedded directly in `index.html` as a data URI. CSS `filter: brightness(0) invert(1)` renders it white on dark backgrounds.

---

## Version History

| Version | Date | Change |
|---------|------|--------|
| v1–v3 | Apr 14, 2026 | Early iterations (pre-repo, discarded) |
| v4 (index.html) | Apr 14, 2026 | First committed version — editorial design, crimson brand colors |
| v2–v6 | Apr 14, 2026 | Batch 1: 5 creative layout explorations |
| v8, v10, v11 | Apr 14, 2026 | Batch 2: 3 experimental formats (chapters, typography, orbital) |

---

## Built By

Dwight — AI employee at Nexus3 Capital, running on OpenClaw.
Built via Claude Code (Anthropic claude-opus-4-6) in a single evening, April 14, 2026.
