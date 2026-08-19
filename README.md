### Han Yesung

**Product-minded developer. Seoul, Korea.**

I build small software for specific people. Most of my design time goes into what an app
*refuses* to store — the privacy model is part of the product, not a page in the settings menu.

---

### Currently building

**[gomsin-log](https://github.com/yesung23/gomsin-log)** · 곰신로그 — [gomsin-log.vercel.app](https://gomsin-log.vercel.app)

A private 1:1 daily log for couples separated by Korean military service, where replies can be
days apart. Photos, video, voice notes and one-line text land on a shared timeline that neither
person has to answer in real time.

`React 19` `TypeScript` `Vite` `Tailwind v4` `Supabase (Postgres + RLS)` `Capacitor 7`

---

### Design decisions I'd defend

**The schema declines data.** Onboarding collects a nickname, a role, and service dates.
It deliberately does not collect real name, gender, birth date, rank, unit name, unit location,
or military ID — for a product built around soldiers, the smallest safe record is the whole point.

**Privacy enforced twice.** Entries default to shared; a per-entry private flag pulls a record out
of the partner's timeline, calendar, and summaries. That rule lives in Postgres RLS policies *and*
in a client-side filter, so a UI bug can't leak a private entry and neither can a bad query.

**Offline is the normal case, not the error case.** Records queue in a per-account IndexedDB outbox
and sync when the connection comes back — because the people using this are often the ones without
reliable signal.

**Not an AI product.** There is one small optional summary card. Everything else is a plain,
time-ordered log, because the value here is the record existing, not a model interpreting it.

---

### Toolkit

- **Product surface** — React, TypeScript, Vite, Tailwind, React Router
- **Data & backend** — Supabase, Postgres, row-level security, Edge Functions, IndexedDB
- **Shipping** — Capacitor (Android / iOS from one codebase), Vercel
- **Quality** — Vitest, Playwright, scripted release checks for native permissions and deep links
- **Working method** — AI-assisted engineering, with the constraints and handoff notes kept in-repo

---

<sub>Public repos here are the ones I'm willing to have read line by line. Some work stays private.</sub>
