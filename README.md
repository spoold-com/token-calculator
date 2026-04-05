# Token calculator & cost — LLM token counter (cl100k / o200k / approx)

[![Open tool](https://img.shields.io/badge/Open-Token%20calculator-6366f1?style=for-the-badge&logo=googlechrome&logoColor=white)](https://spoold.com/tools/token-calculator)
[![Site](https://img.shields.io/badge/spoold.com-live-22c55e?style=flat-square&logo=googlechrome&logoColor=white)](https://spoold.com/tools/token-calculator)
![Free](https://img.shields.io/badge/price-free-22c55e?style=flat-square)
![Sign-up](https://img.shields.io/badge/sign--up-not%20required-64748b?style=flat-square)
[![Source](https://img.shields.io/badge/code-open%20source-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/thespoold/spoold)

[![Next.js](https://img.shields.io/badge/Next.js-16-000000?style=flat-square&logo=nextdotjs&logoColor=white)](https://nextjs.org)
![Client-side](https://img.shields.io/badge/counting-client--side-0ea5e9?style=flat-square)

**Free [LLM token calculator](https://spoold.com/tools/token-calculator)**: paste text to count **tokens** with **tiktoken-style** encodings (**cl100k_base**, **o200k_base**) or a fast **approximate** rule (UTF-8 bytes ÷ 4). See **words**, **characters**, and **illustrative** USD estimates for **input** and **expected output** tokens. **Token visualization** shows how the text splits into pieces (with preview / expand limits). **Compare costs** table pits illustrative rates across models. **No server round-trip** for counting — runs in the browser; **localStorage** persists your draft (`spoold-token-calculator`). **Not a billing quote** — confirm pricing with your provider.

**Live tool:** [spoold.com/tools/token-calculator](https://spoold.com/tools/token-calculator)

---

## Table of contents

- [What this tool is for](#what-this-tool-is-for)
- [Who searches for this (keywords)](#who-searches-for-this-keywords)
- [Features](#features)
- [How to use](#how-to-use)
- [Rules, limits & disclaimers](#rules-limits--disclaimers)
- [Related tools](#related-tools)
- [Tech stack](#tech-stack)
- [Repository](#repository)

---

## What this tool is for

Use this **online token counter** when you need to:

- **Estimate prompt size** before calling an API (especially when your stack uses OpenAI-style tokenization).
- **Compare cl100k vs o200k** counts on the same text (models and APIs differ).
- **Ballpark cost** from illustrative $/1M **input** and **output** rates plus an **expected output token** count.
- **See token boundaries** in the text via the visualization (helpful for debugging long prompts).

Part of **[Spoold](https://spoold.com)** — web and developer utilities in one place.

---

## Who searches for this (keywords)

**llm token calculator**, **token counter online**, **gpt token counter**, **openai token calculator**, **tiktoken calculator**, **cl100k token counter**, **o200k tokenizer**, **prompt token calculator**, **token cost estimator**, **characters to tokens**, **chatgpt token calculator**.

---

## Features

| Area | What you get |
|------|----------------|
| **Tokenizers** | **Approximate** (bytes ÷ 4), **cl100k_base**, **o200k_base** via **js-tiktoken** (exact modes load on the client). |
| **Stats** | Token count, word count, characters (with / without spaces). |
| **Cost estimate** | Dropdown of **illustrative** model rates ($/1M in & out) plus **Custom** fields; **expected output tokens** for output-side estimate. |
| **Visualization** | Colored token pieces; **preview** cap with **show all** up to a **hard max** (see limits). |
| **Compare costs** | Side-by-side illustrative totals for multiple models from the same input/output assumptions. |
| **Persistence** | **localStorage** key `spoold-token-calculator` saves text, tokenizer, model selection, custom rates, and expected output tokens. |
| **Guide** | On-page SEO/guide section (`#token-calculator-guide`) for deeper context. |

---

## How to use

1. Open **[Token calculator & cost](https://spoold.com/tools/token-calculator)**.
2. Choose **Tokenizer** (approx, cl100k, or o200k).
3. Optionally pick a **Model** for the $ estimate (or **Custom** and edit $/1M).
4. Set **Expected output tokens** if you want an output cost line.
5. Paste or type text in the editor; read **tokens**, **cost** summary, **visualization**, and **compare** table.

---

## Rules, limits & disclaimers

- **Client-only counting:** Exact tiktoken encodings run in the browser; there is **no** dedicated API for token counts in this tool.
- **Visualization caps:** Piece list is shown in **preview** up to **400** tokens by default; expanding uses the same pipeline capped at **8000** tokens (`TOKEN_LIST_VIZ_PREVIEW` / `TOKEN_LIST_HARD_MAX` in `@/lib/token-budget-count`).
- **Approximate mode:** **Not** equivalent to provider billing; useful for quick mental math.
- **Prices:** All $/1M values are **illustrative** (`@/lib/token-calculator-pricing`). **Always** verify current pricing on the vendor’s site.

---

## Related tools

- **[Token & context budget](https://spoold.com/tools/token-budget)** — Split prompt into system / user / RAG / extra and check against a **context window** (same tokenizer modes).
- **[LLM RAM / VRAM](https://spoold.com/tools/llm-ram)** — GPU memory planning.
- **[Token speed simulator](https://spoold.com/tools/token-speed)** — Throughput / latency feel.

---

## Tech stack

- **Next.js** App Router — page at `src/app/tools/token-calculator/page.tsx`, UI in `token-calculator-client.tsx`.
- **js-tiktoken** for **cl100k_base** / **o200k_base** encoding (shared helpers in `@/lib/token-budget-count`).
- **React** client components for editor, visualization, and compare panel.

---

## Repository

**[github.com/thespoold/spoold](https://github.com/thespoold/spoold)** — `pnpm install && pnpm dev`, then open `/tools/token-calculator`.

---

**Spoold** — *Paste. Detect. Do.* · [spoold.com](https://spoold.com)
