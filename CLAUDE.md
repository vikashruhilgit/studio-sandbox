# CLAUDE.md

**studio-sandbox** is a throwaway repo for Loomwright Studio's probes (p14, p15). Its changes are tiny on purpose: each story under `stories/` or `stories-p15/` asks for one small shell script.

## Tech stack

- Bash scripts only. No package manager, no build step, no dependencies.

## Directory structure

| Path | What |
|---|---|
| `*.sh` (repo root) | The scripts the stories ask for. Each lives at the repo root. |
| `stories/`, `stories-p15/` | Requirement files, one story each, read by Loomwright `/automate`. |
| `.github/workflows/ci.yml` | The `ci` check: `bash -n` on every root `*.sh`. |

## Key patterns

- A script prints exactly what its story says and exits 0. Keep it to a few lines.
- Change only the files a story names. Nothing under `.github/`, no secrets.
- `ci` is the only required check on `main`. Run it locally with `for f in *.sh; do bash -n "$f"; done`.
- Base branch is `main`.
