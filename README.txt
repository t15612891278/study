# Study — CFA & CPA Mastery App

A self-paced study tool for CFA L1/L2/L3, CPA FAR/AUD/REG/BEC, and IFRS mastery.
Narrative lessons → quiz questions → Anki spaced repetition memory review.

---

## Why You Need Your Own Supabase

This app is designed so that **you own your own data**. Here is why:

- Your study progress, email, and account are stored in **your own database** — not mine
- I never see your data, cannot access it, and have no liability for it
- If this app ever goes offline, your data stays in your Supabase account forever
- You control who has access and can delete your data anytime
- This is the most privacy-respecting architecture possible for a web app

Think of it like email — I built the app, you bring your own mailbox.

---

## How to Set Up Supabase (Free, 10 minutes)

### Step 1 — Create a Supabase account
1. Go to [supabase.com](https://supabase.com)
2. Click **Start your project** — sign up with GitHub or email
3. Click **New project**
4. Name it `study`, choose a region close to you, set a database password
5. Click **Create new project** — wait about 2 minutes

### Step 2 — Create the progress table
1. In your Supabase project, click **SQL Editor** (left sidebar)
2. Paste and run this SQL:

```sql
create table progress (
  user_id text primary key,
  data jsonb,
  updated_at timestamptz default now()
);
```

### Step 3 — Get your credentials
1. Click **Settings** → **API**
2. Copy your **Project URL** (looks like `https://xxxx.supabase.co`)
3. Copy your **Publishable / anon key** (starts with `sb_publishable_` or `eyJ...`)

### Step 4 — Connect to the app
1. Open the Study app
2. On the login screen, tap **⚙️ Setup Cloud Save (Supabase)**
3. Paste your Project URL and key
4. Tap **Save & Continue**
5. Create your account with email and password

Your progress now saves to your own PostgreSQL database automatically.

---

## Database Size

Extremely small. One row per user containing a JSON object of your progress.
Supabase free tier gives you 500MB — enough for roughly 1 million users at this schema size.

---

## Local Mode (No Supabase)

If you skip Supabase setup, the app saves progress in your browser's local storage.
This works fine but progress will not sync across devices and will be lost if you clear your browser.
