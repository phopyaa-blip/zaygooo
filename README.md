# مندوبك — Mandobak

Egyptian delivery platform with three surfaces: Customer App, Driver App, and Company Dashboard.

## Tech Stack

- **Frontend:** React 19 + Vite 7, Tailwind CSS, shadcn/ui, Cairo font
- **Backend:** Express 5 (serverless via Vercel Functions)
- **Database:** PostgreSQL + Drizzle ORM (Supabase-hosted)
- **Language:** TypeScript 5.9 (full monorepo)
- **Package manager:** pnpm workspaces

## Features

- **Customer App** (`/`) — Browse shops & menus, place orders, track delivery, live support chat
- **Driver App** (`/driver`) — Accept/deliver/transfer orders, set availability, chat with company
- **Company Dashboard** (`/company`) — Kanban orders board, manage shops & drivers, send notifications
- **PWA** — Installable on Android via Chrome "Add to Home Screen"

## Setup (3 steps)

```bash
# 1. Install dependencies
pnpm install

# 2. Copy env file and fill in your values
cp .env.example .env.local

# 3. Push DB schema and seed demo data
pnpm --filter @workspace/db run push
npx tsx scripts/seed.ts
```

## Environment Variables

| Variable | Description |
|---|---|
| `DATABASE_URL` | PostgreSQL connection string |
| `SUPABASE_DATABASE_URL` | Supabase Postgres URL (with `?sslmode=require`) |
| `VITE_SUPABASE_URL` | Supabase project URL (for storage) |
| `VITE_SUPABASE_ANON_KEY` | Supabase anon/public key (for storage) |
| `PORT` | API server port (default: 8080) |
| `LOG_LEVEL` | Pino log level (default: info) |

> **Note:** Set all variables in Vercel → Project Settings → Environment Variables before deploying.

## Run Locally

```bash
# API server (port 8080)
PORT=8080 pnpm --filter @workspace/api-server run dev

# Frontend (port 5000)
PORT=5000 BASE_PATH=/ pnpm --filter @workspace/mandobak run dev
```

## Deploy to Vercel

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/your-org/mandobak)

1. Import repo into Vercel
2. Set all environment variables (see table above)
3. Vercel auto-detects `vercel.json` — build runs `pnpm run vercel:build`

## Build Locally

```bash
pnpm run vercel:build
# Build log: vite build = SUCCESS ✓
```

## Android / PWA

The app is installable as a PWA on Android:

1. Open the deployed URL in **Chrome Mobile**
2. Tap the browser menu → **"Add to Home Screen"**
3. The app installs with the Mandobak orange icon and runs in standalone mode

## Project Structure

```
artifacts/
  api-server/    Express backend (Vercel serverless function via api/index.ts)
  mandobak/      React + Vite frontend
lib/
  api-spec/      OpenAPI spec + Orval codegen config
  api-client-react/  Generated React Query hooks
  api-zod/       Generated Zod validators
  db/            Drizzle ORM schema + migrations
scripts/
  seed.ts        Demo data seeder
api/
  index.ts       Vercel serverless entry point
```
"# zaygooo" 
"# zaygooo" 
