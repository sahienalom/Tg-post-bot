# 📢 Post Maker Bot

**A premium Telegram bot for creating and publishing rich channel posts.**  
Connect your channels, compose posts with media and inline buttons, preview them live, and publish — all from a clean, fast bot interface.

---

## ✨ Features

| Feature | Details |
|---|---|
| **Channel Management** | Connect multiple channels, switch active channel, disconnect anytime |
| **Post Wizard** | Text · Photo · Video · Animation · Audio · Voice · Document · Sticker |
| **Button Builder** | URL and WebApp buttons · Primary / Success / Danger styles · Flexible row layout |
| **Live Preview** | See exactly how your post will look before it goes live |
| **Draft System** | Auto-save drafts, resume later, rename, delete |
| **Permission Checks** | Bot verifies it's admin with all required permissions before every publish |
| **Multi-Channel** | Unlimited channels per user; one Active at a time |

---

## 🚀 Quick Start

### 1. Clone the repository

```bash
git clone https://github.com/yourname/post-maker-bot.git
cd post-maker-bot
```

### 2. Create a virtual environment

```bash
python -m venv .venv
source .venv/bin/activate        # Linux / macOS
.venv\Scripts\activate.bat       # Windows
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure environment variables

```bash
cp .env.example .env
```

Open `.env` and set your bot token:

```env
BOT_TOKEN=your_token_from_botfather
```

### 5. Run the bot

```bash
python -m bot.main
```

---

## 📁 Project Structure

```
post-maker-bot/
├── bot/
│   ├── config/          # pydantic-settings config from .env
│   ├── database/        # aiosqlite connection, schema init, DAOs
│   ├── handlers/        # aiogram routers (one file per feature)
│   ├── keyboards/       # InlineKeyboardMarkup builders
│   ├── middlewares/     # UserMiddleware (auto-registration)
│   ├── models/          # Pydantic domain models
│   ├── services/        # Business logic (channel, post, draft)
│   ├── states/          # FSM StatesGroups
│   ├── utils/           # Validators, formatters, helpers
│   └── main.py          # Entry point
├── .env.example
├── requirements.txt
└── README.md
```

---

## ⚙️ Environment Variables

| Variable | Required | Default | Description |
|---|---|---|---|
| `BOT_TOKEN` | ✅ | — | Telegram Bot Token from @BotFather |
| `DATABASE_PATH` | ❌ | `bot.db` | Path to the SQLite database file |
| `LOG_LEVEL` | ❌ | `INFO` | Python logging level |

---

## 🔑 Required Bot Admin Permissions

When connecting a channel, the bot must be an **Administrator** with:

- `can_post_messages`
- `can_edit_messages`
- `can_delete_messages`
- `can_manage_chat`

---

## 📖 Bot Commands

| Command | Description |
|---|---|
| `/start` | Open the dashboard |
| `/connect @channel` | Connect a channel directly |
| `/help` | Show the help message |

---

## 🛠️ Tech Stack

- **Python 3.11+**
- **aiogram 3.x** — async Telegram Bot framework
- **SQLite + aiosqlite** — lightweight async database
- **Pydantic v2** — data validation and settings
- **python-dotenv / pydantic-settings** — environment configuration
- **AsyncIO** — fully asynchronous throughout

---

## 🗄️ Database Schema

```sql
users     — telegram_id, name, username, joined_at
channels  — user_id, channel_id, channel_name, username, is_active
drafts    — user_id, name, content_type, file_id, caption, buttons_json
posts     — user_id, channel_id, message_id, created_at
```

---

## 📜 License

MIT © 2024 — see [LICENSE](LICENSE)
