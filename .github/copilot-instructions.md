<!-- .github/copilot-instructions.md - guidance for AI coding agents -->
# Copilot instructions for Udoka Fm

Purpose: Provide concise, actionable rules so an AI coding agent can be immediately productive in this repository.

**Big Picture**
- Single-page static site: the application lives in [index.html](index.html). There is no build system, package manager, or server code in the repo.
- Primary data flow: DOM markup -> optional client-side JS injected at end of `<body>` -> browser renders. Keep changes local to `index.html` or add assets under an `assets/` folder.

**How to run / preview**
- Open [index.html](index.html) directly in a browser for quick checks.
- For a local HTTP server (recommended for fetch/XHR or module scripts):

```bash
python -m http.server 8000
# or
npx http-server . -p 8000
```

Then visit http://localhost:8000

**Project-specific conventions**
- No frameworks: prefer vanilla HTML/CSS/JS. If adding JS, place files under `assets/js/` and include scripts at the end of `<body>`.
- Keep markup minimal and accessible: include `lang`, `meta` viewport, and UTF-8 charset as in [index.html](index.html).
- Favor small, self-contained changes: this repo is tiny — avoid scaffolding a large build system unless the user requests it.

**Editing patterns & examples**
- To add interactive behavior, create `assets/js/main.js` and reference it just before `</body>`:

```html
<script src="assets/js/main.js"></script>
</body>
```

- To add styles, use `assets/css/` and link in `<head>`.

**Tests / CI / Tooling**
- None present. Do not assume unit tests or linters. If you add tooling, update this file with the exact commands and new files introduced.

**Integration & external dependencies**
- Currently there are no external service integrations. When introducing APIs or third-party SDKs, add a short note here describing the endpoint, auth method, and where credentials should be stored (never commit secrets).

**AI agent rules & generation guidance (concrete)**
- Prefer minimal, human-readable code changes — one small file change per PR.
- Avoid introducing build tooling or dependencies without explicit user approval.
- If the change touches visuals, include a short manual test checklist (browser steps) in the PR description.
- When suggesting code, include the exact file path(s) to modify and a short (1-2 line) rationale.

If anything above is unclear or you'd like the agent to follow stricter coding styles, tell me what to add and I will update this file.
