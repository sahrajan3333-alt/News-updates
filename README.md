# THE DAILY BRIEF (दैनिक ब्रिफिङ)
## Multilingual News Intelligence & Daily Briefing Platform

> **"Not more news. Better understanding of the world."**  
> *बढी समाचार होइन। संसारको राम्रो बुझाइ।*

---

## 🌟 Overview

**THE DAILY BRIEF** is an editorial news intelligence platform designed specifically to counter information overload, repetitive headlines, and sensational clickbait. Curated for readers in Nepal and globally, it transforms breaking news into structured, verified, and contextual intelligence.

### Core Distinctions
- **Why It Matters Analysis**: Every story breaks down *What happened*, *Why it is important*, *Who is affected*, and *Future consequences*.
- **Multilingual By Architecture**: Full support for English and Nepali Devanagari typography with Unicode safety and bidirectional state persistence.
- **5-Minute Daily Briefing**: A high-density morning intelligence briefing providing the top 7 essential developments across Nepal and global desks.
- **Editorial Fact-Checking & Moderation Queue**: Sensitive claims (armed conflicts, casualty counts, elections) are quarantined for human verification before public syndication.
- **Source Transparency & Attribution**: Every brief prominently attributes original reporting publishers (The Kathmandu Post, BBC, Reuters, NASA, etc.) and provides direct links without replicating full copyrighted articles.
- **No Behavioral Tracking**: Zero ad-tech surveillance pixels, clean typography, light and dark themes with persistent user preference.

---

## 🏗️ Technology Stack

| Layer | Technology |
|---|---|
| **Frontend Framework** | React 19 + TypeScript + Vite |
| **Styling & Design System** | Tailwind CSS (Custom editorial palette `#153D32`, `#C6A76B`, `#F7F7F2`) |
| **Typography** | Playfair Display (Serif headings), Inter (Clean body), Noto Sans Devanagari (Nepali Unicode) |
| **Routing** | React Router v7 with dynamic desk parameters and scroll restoration |
| **State & Data Fetching** | TanStack React Query v5 + Context API |
| **Icons** | Lucide React |
| **Backend & Storage** | Supabase (PostgreSQL 15+, pg_trgm for search, Row Level Security) |
| **Serverless Workers** | Supabase Edge Functions (Deno) for RSS ingestion, AI summarization, and translation |
| **AI Layer** | OpenAI / Groq / Anthropic compatible API integration |

---

## 📁 Project Architecture

```
news-update/
├── src/
│   ├── components/
│   │   ├── layout/         # Header, Navigation, Footer, Mobile Drawer
│   │   ├── sections/       # WorldToday, TopStories, LatestUpdates, WhyItMatters, DailyKnowledge
│   │   └── ui/             # NewsCard, FeaturedCard, ImportanceBadge, CategoryBadge, ReadingTime
│   ├── contexts/           # ThemeContext, LanguageContext, AuthContext, BookmarkContext
│   ├── hooks/              # Reusable hooks
│   ├── i18n/               # en.ts, ne.ts, index.ts (Devanagari translations)
│   ├── lib/                # constants.ts (Categories, Importance levels), queryClient.ts
│   ├── pages/
│   │   ├── HomePage.tsx               # Primary editorial newspaper grid
│   │   ├── ArticlePage.tsx            # Full brief, Why It Matters, Sources & Citations
│   │   ├── DailyBriefingPage.tsx      # 5-minute concise summary experience
│   │   ├── SearchPage.tsx             # Multi-filter search (desk, priority, geography)
│   │   ├── StoryTimelinePage.tsx      # "Follow the Story" chronological progression
│   │   ├── AdminPage.tsx              # Editorial moderation queue, source manager, translation editor
│   │   ├── CategoryDeskPage.tsx       # Dynamic desk engine
│   │   ├── NepalPage.tsx              # National governance, economy, policy
│   │   ├── WorldPage.tsx              # International diplomacy & multilateral relations
│   │   ├── PoliticsPage.tsx           # Neutral legislative & electoral coverage
│   │   ├── WarConflictsPage.tsx       # Verified conflict reporting (anti-sensationalism)
│   │   ├── ClimateEnvironmentPage.tsx # Himalayan glaciers, GLOF, air quality, biodiversity
│   │   ├── ScienceTechPage.tsx        # Peer-reviewed research, AI compute, space
│   │   ├── EconomyPage.tsx            # Inflation, remittances, central bank policy
│   │   ├── SportsPage.tsx             # Nepali cricket, football, international tournaments
│   │   ├── ExplainersPage.tsx         # Educational knowledge primers
│   │   └── [8 Policy Pages]          # About, Mission, Editorial, Corrections, Privacy, Terms, Sources, Contact
│   ├── services/           # supabase.ts, newsService.ts, mockData.ts
│   ├── types/              # Complete TypeScript interfaces
│   └── utils/              # formatDate.ts, readingTime.ts, textUtils.ts, cn.ts
├── supabase/
│   ├── schema.sql          # Complete PostgreSQL schema with 11 tables, indexes, and RLS policies
│   ├── edge-functions/     # fetch-rss, process-news, translate
│   └── README.md           # Database setup guide
├── .env.example
├── index.html
├── tailwind.config.js
└── package.json
```

---

## 🚀 Getting Started

### 1. Prerequisites
- Node.js 18+ or 20+
- npm or pnpm

### 2. Installation
```bash
# Clone or navigate to the directory
cd "news update"

# Install dependencies
npm install
```

### 3. Environment Setup
Copy the example environment configuration:
```bash
cp .env.example .env
```

Edit `.env` to configure your credentials:
```env
# Supabase Configuration
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_ANON_KEY=your_public_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_service_role_key

# AI Provider (OpenAI, Groq, or any OpenAI-compatible endpoint)
AI_API_KEY=your_ai_key
AI_MODEL=gpt-4o-mini
AI_BASE_URL=https://api.openai.com/v1

# App URL
VITE_APP_URL=http://localhost:5173
```

> **Note**: If Supabase credentials are not provided, the platform automatically starts in **Demonstration Mode**, providing 50+ realistic curated briefings across all 9 desks with full bilingual translations.

### 4. Running Locally
```bash
npm run dev
```
Open [http://localhost:5173](http://localhost:5173) in your browser.

### 5. Building for Production
```bash
npm run build
npm run preview
```

---

## 🗄️ Database Setup (Supabase)

1. Create a new Supabase project at [supabase.com](https://supabase.com).
2. Open the **SQL Editor** in the Supabase Dashboard.
3. Paste and run the entire contents of `supabase/schema.sql`.
4. This will create:
   - Tables: `categories`, `news_sources`, `news_articles`, `story_clusters`, `story_timelines`, `article_translations`, `user_profiles`, `bookmarks`, `admin_users`, `editorial_reviews`, `fetch_logs`
   - Row Level Security (RLS) policies allowing public read of published stories and restricting editorial functions to admins.
   - Seed data for 9 editorial desks and 10 default verified news sources.

---

## 🛡️ Editorial Standards & Trust Principles

1. **Non-Sensationalism**: We avoid dramatic clickbait headlines, hyperbolic adjectives, and speculative claims.
2. **War & Conflict Protocol**: We never publish unconfirmed casualty figures as established facts. Battlefield claims must cite the exact reporting military or monitoring organization.
3. **Transparent Importance Scoring**: Stories are rated as **CRITICAL**, **IMPORTANT**, or **WORTH KNOWING** based on human consequence, economic impact, and long-term significance—never clicks or ad revenue.
4. **Correction Accountability**: Any factual revisions are published with an explicit transparency note and timestamp.

---

## 📄 License & Attribution
Published under standard open news aggregation principles. Original article rights belong to their respective publishers. All summaries, analyses, and translations synthesized by THE DAILY BRIEF.

