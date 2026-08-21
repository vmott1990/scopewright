# Scopewright

A small tool that turns raw discovery-call notes into a first-draft Statement of Work — numbered clauses, not a chat transcript.

**[Live demo →]

## Why I built this

Scoping is one of the highest-friction, most repetitive steps in any services engagement — client-side or advisory-side. The gap between "we had a good discovery call" and "here's a defensible first-draft SOW" usually costs an hour and a blank page. This closes most of that gap: paste notes in, get a structured draft out in the same shape a senior PS lead would write by hand.

It's deliberately narrow. It doesn't try to replace judgment on pricing, risk, or commercial terms — it removes the blank-page problem so a human can spend their time reviewing and negotiating instead of drafting from scratch.

## How it works

- Single HTML file. No framework, no build step, no backend.
- Calls the Claude API with a system prompt that returns structured JSON:
  `overview`, `objectives`, `scope_in`, `deliverables`, `assumptions`, `timeline`, `out_of_scope`, `success_criteria`.
- The prompt explicitly forbids inventing numbers, names, or commitments that aren't in the source notes — thin sections come back as `"To be confirmed with client"` rather than a plausible-sounding guess. Getting an LLM to say "I don't know" convincingly in a business document is most of the actual design work here.
- The JSON is rendered client-side as a numbered document (1.0, 1.1, 1.2…) styled like a real engagement letter, not a raw model response.

## Try it

Click **Load example** in the app for a pre-filled pre-TGE tokenomics / market maker advisory scenario, or paste your own notes.

To run it yourself with your own Anthropic API key, you'd need to route the `fetch` call in `index.html` through a small server-side proxy (Cloudflare Worker, Vercel function, etc.) rather than calling the API directly from the browser — never ship an API key in client-side JS.

## Stack

Vanilla HTML/CSS/JS, Claude (Sonnet), Google Fonts. No dependencies.

## License

MIT
