# LangGraph Support Routing

A minimal LangGraph workflow that routes users to different support paths based on their tier (`vip` vs `standard`).

## Setup

1. Create and activate a virtual environment:
   ```bash
   python -m venv venv
   source venv/Scripts/activate  # Windows
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Create a `.env` file with your API keys (see below). **Do NOT commit `.env` to version control.**

## Running

```bash
python app.py
```

## Environment Variables

Create a `.env` file in the project root:

```
OPENAI_API_KEY=your_key_here
```

> **Warning:** Never commit your `.env` file. It is listed in `.gitignore` to prevent accidental exposure of secrets.

## How It Works

- `SupportState` tracks conversation messages, user tier, escalation flag, and issue type.
- `check_user_tier_node` detects if the user is VIP based on message content.
- `route_by_tier` routes VIP users to `vip_agent` and standard users to `standard_agent`.
- VIP users get priority support with no escalation; standard users are flagged for escalation.
