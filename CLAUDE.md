# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Commands

```bash
npm run dev       # start dev server (Vite, localhost:5173)
npm run build     # build to docs/ (used for GitHub Pages deployment)
npm run lint      # ESLint
npm run preview   # preview the production build locally
```

There are no tests.

## Architecture

This is a React 19 + Vite app styled with [PicoCSS](https://picocss.com/). It's the exercise project for the LinkedIn Learning course "Claude Code 4: Agentic Coding for Professional Developers".

**Data flow:** `App.jsx` fetches `public/cast.json` on every render (no dependency array in `useEffect`) and passes the resulting array down as props. Member selection state (`memberInfo`) lives in `App` and is threaded to `Nav` (dropdown picker) and `ListCast` (card grid), both of which call `onChoice(member)` to set it. When set, `Modals` renders over the page.

**Theme:** `ToggleTheme` cycles through `auto → light → dark → auto`, persists to `localStorage`, and applies the value via `data-theme` on `<html>`. PicoCSS reads that attribute natively.

**Build output:** Vite is configured with `base: './'` and `outDir: 'docs'`, so `npm run build` writes to `docs/` for GitHub Pages hosting.

**Branches:** The repo has per-lesson branches named `CHAPTER#_MOVIE#` (e.g. `02_03b` = beginning, `02_03e` = end). `main` is the final course state.
