# 📝 Annotated Reader

Open a Markdown document, highlight what matters, and leave comments anchored to the exact words — then hand the whole thing off, privately, in a single file or link.

**Live:**
- ▲ Vercel — https://md-comments.vercel.app
- 🐙 GitHub Pages — https://tetiioo.github.io/annotated-reader/

A single, dependency-light `index.html`. No build step, no backend, no account.

---

## What it does

- **Chapters** — splits any `.md` into chapters from its `#`/`##` headings, with a sidebar table of contents.
- **Highlight or comment** — select text to get a toolbar: pick a highlight color (yellow / green / pink / blue) or attach a comment. Comments are anchored to the exact words and marked with a 💬 cue.
- **Review queue** — a Comments tab lists every note; the viewer has Prev/Next (and `Alt`+`↑`/`↓`) to step through feedback in document order.
- **Robust anchoring** — comments re-locate by quoted text when a document changes; unfindable ones are clearly flagged as orphaned rather than drifting onto the wrong sentence.

## Sharing — three ways

| Method | Best for | Privacy |
|---|---|---|
| **🔒 Download .md with comments** | Sending a confidential doc back and forth | Comments are tucked into a hidden HTML comment inside the `.md`; invisible in any other Markdown viewer. **Nothing is uploaded — files are read entirely in your browser.** |
| **Save / Open project** | Archiving or re-importing later | A `.json` with the document + all comments. Local file. |
| **🔗 Copy share link** | Quick send for non-sensitive docs | Document + comments are compressed into the URL fragment (never sent to a server, but the link text itself travels through wherever you paste it). |
| **Export as webpage** | A standalone read-only artifact | One self-contained HTML file that opens anywhere, offline, forever. |

## Privacy

Your document never leaves your device. Files are read in-browser via the `FileReader` API — there is no server upload. The only network requests are the three CDN libraries the app itself loads. You can verify: open the browser Network tab while opening a file (zero requests), or load the page once and go offline — everything still works.

## Run locally

```bash
node server.js   # serves index.html on http://localhost:4599
```
Or just open `index.html` in a browser.

## Built with

[marked](https://github.com/markedjs/marked) (Markdown), [DOMPurify](https://github.com/cure53/DOMPurify) (sanitization), and [lz-string](https://github.com/pieroxy/lz-string) (share-link compression) — loaded from CDN. Everything else is vanilla JS/CSS in one file.

## Hardening

The flows were refined over five rounds of structured review (product design, product management, engineering), covering data-loss prevention (no silent document truncation, storage-quota safety), correctness (overlapping-selection and duplicate-quote anchoring), security (Markdown sanitization, safe export embedding), and accessibility (keyboard operation, focus management, dark mode, reduced-motion). See the commit history for the per-round changelog.

---

🤖 Built with [Claude Code](https://claude.com/claude-code)
