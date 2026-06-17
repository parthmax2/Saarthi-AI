# Contributing to Saarthi AI

Thanks for helping improve Saarthi AI. This project is a Lucknow-focused commute-planning agent built with FastAPI, deterministic tool calls, LLM synthesis, and MongoDB-backed memory.

## Local setup

```bash
python -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements-dev.txt
cp .env.example .env
uvicorn main:app --reload
```

Fill in `.env` with real API keys before testing live traffic, geocoding, LLM, or MongoDB flows. Never commit secrets.

## Development workflow

1. Create a small branch for the change.
2. Keep changes scoped to the feature, bug fix, or documentation update.
3. Add or update tests when behavior changes.
4. Run formatting, linting, and tests before opening a pull request.

Recommended checks:

```bash
black app main.py
isort app main.py
flake8 app main.py
pylint app main.py
mypy app main.py
python -m pytest
```

## Code style

- Prefer clear, deterministic tool behavior before LLM narration.
- Keep API failures graceful; live services should not crash the full user flow.
- Scrub secrets from logs and errors with `app.netutil` helpers where applicable.
- Keep module docstrings focused on what the module owns and how it fits the agent pipeline.
- Use type hints for new public functions when practical.

## Pull request checklist

- Runtime dependencies belong in `requirements.txt`; test and lint tooling belongs in `requirements-dev.txt`.
- `.env.example` is updated for any new configuration variable.
- New user-visible behavior is documented in `README.md` when relevant.
- Tests pass locally, or the PR clearly explains what could not be run.
