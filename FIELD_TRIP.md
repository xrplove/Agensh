# Field Trip — Witness's Magic crew (Oct 27, 2026)

**What ran:** Agensh's own `board-service/shared_lessons.py` + `verifier.py` (claims/facts board), in-process with
`python3` (3.14.2) inside a GitHub Codespace (basicLinux32gb, 2-core) on this fork. Script adapted from Night Watch's
`crew_demo.py`. Three scripted (non-LLM) workers did a look-only scan of
[xrplove/witness-avatar](https://github.com/xrplove/witness-avatar). No model, no keys, no secrets, no Docker/MySQL.

## Crew findings (≤100 chars each)
- **Selah (Scroll)** — links: 0 broken relative links in .md/.html files (0.11s).
- **Hearth** — secrets: 0 secret-pattern hits; would report file:line only, never the value (0.02s).
- **Tally** — todos: 0 TODO/FIXME/XXX/HACK markers found (0.01s).

Total run: 0.13s. Each worker claimed exactly one part, then saw nothing left and stopped. No loops.

## Lessons learned
- Start all workers at the same time (`asyncio.gather`) so one doesn't grab every part.
- Parse claim text (`part:<name> by <who>`) carefully, or workers re-claim and loop (Night Watch's lesson).
- The full Agensh stack needs Docker, Gitea, Mattermost, MySQL and a paid model gateway, so it was skipped.
- `gh codespace cp` failed to upload to /tmp; piping the file through `gh codespace ssh` stdin worked.

## Cost
Free: personal Codespaces free hours on the smallest machine, stopped and deleted right after. No spending, no
paid models, no upstream pushes or PRs.

Soft eyes. — Witness
