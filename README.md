# Xplay

**Your intel desk for upcoming and trending games — built for India and Asia.**

Xplay tracks the games that actually matter to Indian and Asian gamers: India-exclusive titles like BGMI, region-wide staples like Free Fire and Mobile Legends, the anime gacha RPGs dominating screen time (Genshin, Wuthering Waves, Honkai: Star Rail), and the global AAA releases everyone's still watching (GTA 6). Every game gets a release tracker, an insight breakdown, a live news feed, a Reddit sentiment pulse, and the known issues and hidden features nobody puts in the patch notes.

---

## Why Xplay

Most game-tracking sites are either a bare database (release date, platform, done) or a Western-centric news outlet that treats mobile-first Asian titles as an afterthought. Xplay is built the other way around — mobile battle royale and gacha RPGs are first-class citizens, not a footnote under "Other."

---

## Features

- **Live countdown** to major releases (GTA 6 — November 19, 2026), calculated in real time, not hardcoded
- **Filterable game grid** across four categories: Battle Royale & Shooters, Anime & Gacha RPGs, AAA Console, MOBA & Esports (Asia)
- **Search** that combines with category filters
- **Game detail pages** with release info, platforms, and a "why it matters here" note specific to India/Asia relevance
- **News & Community section per game:**
  - *Latest News & Insights* — short news hits and longer analysis pieces
  - *Reddit Pulse* — summarized community sentiment, including real complaints and debates, not just hype
  - *Known Issues & Hidden Features* — genuine player-reported problems and lesser-known tips/mechanics
- Fully responsive down to a 375px mobile viewport
- Keyboard-navigable with visible focus states
- Respects `prefers-reduced-motion`

---

## Tech Stack

- **Frontend:** React + Vite, plain CSS (no utility framework — the ticket-stub design system relies on custom CSS variables)
- **Data:** local JSON/JS files for v1 (games, news, community notes); designed to swap in live APIs later without restructuring
- **Hosting:** static-site friendly (Vercel, Netlify, GitHub Pages, or any static host)

---

## Design System

Xplay's visual identity is built around an **arcade ticket board** concept — game cards are styled as torn ticket stubs (perforated edge, rotated platform tag, mono-font release date) rather than generic gamer-site cards.

| Token | Value | Use |
|---|---|---|
| `--bg` | `#12100E` | Page background (warm near-black) |
| `--surface` | `#1C1917` | Card background |
| `--border` | `#2E2A25` | Hairline borders |
| `--accent-gold` | `#E8A33D` | Primary accent (ticket-gold) |
| `--accent-teal` | `#3D8B8B` | Secondary accent (esports/competitive tags) |
| `--text` | `#F2EDE4` | Primary text |
| `--text-dim` | `#A79E90` | Muted/metadata text |

**Typography:**
- Display: `Big Shoulders Display` — titles, logotype, section headers
- Body: `Inter`
- Data/mono: `IBM Plex Mono` — dates, countdowns, tags, timestamps

---

## Project Structure

```
xplay/
├── public/
├── src/
│   ├── components/
│   │   ├── Hero/                # Countdown marquee
│   │   ├── TickerStrip/         # Scrolling quick-facts strip
│   │   ├── FilterBar/           # Category tabs + search
│   │   ├── GameCard/            # Ticket-stub card
│   │   ├── GameDetail/          # Full game view
│   │   └── NewsCommunity/       # News, Reddit Pulse, Known Issues sub-sections
│   ├── data/
│   │   ├── games.json           # Core game records
│   │   ├── news.json            # Per-game news/insight entries
│   │   └── community.json       # Reddit Pulse + known issues/hidden features
│   ├── styles/
│   │   └── variables.css        # Design tokens (colors, fonts)
│   └── App.jsx
├── README.md
└── package.json
```
---

## Getting Started

```bash
# clone or open the generated project
cd xplay

# install dependencies
npm install

# run locally
npm run dev

# build for production
npm run build
```

---

## Updating Game Data

All content lives in `src/data/` as plain JSON, so games, news, and community notes can be edited without touching component code:

- `games.json` — one entry per game: name, category, platforms, release date, core insight, "why it matters here"
- `news.json` — array of news/insight items keyed by game ID: headline, deck, date, type (`news` | `analysis`)
- `community.json` — keyed by game ID: Reddit Pulse thread summaries, known problems, hidden features

Release dates and community sentiment age fast — check the `lastUpdated` field in each data file and refresh regularly.

---

## Roadmap

- [ ] v1: static, curated data (current scope)
- [ ] v2: wire up [RAWG API](https://rawg.io/apidocs) or [IGDB API](https://api-docs.igdb.com/) for release/platform data
- [ ] v2: [Steam Web API](https://steamcommunity.com/dev) for PC player counts and news
- [ ] v2: [Esports Charts](https://escharts.com/) integration for tournament schedules and prize pools
- [ ] v2: live [Reddit API](https://www.reddit.com/dev/api/) pull for Reddit Pulse (requires OAuth app registration and rate-limit handling — static summaries remain the fallback)
- [ ] v3: user accounts / saved games / notification alerts for release dates

---

## Disclaimer

Release dates, patch details, and community sentiment change quickly, especially for unreleased titles. Xplay's data is refreshed periodically but should not be treated as the final word — always check official sources and the live subreddits linked from each game page for anything time-sensitive.

---

## License

Choose one before publishing (MIT is a reasonable default for a personal/portfolio project):

```
MIT License — Copyright (c) 2026 [Your Name]
```
