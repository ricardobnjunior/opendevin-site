# LinkedIn Post — OpenDevin Launch

## Post

I built an autonomous code pipeline that turns GitHub Issues into merged PRs — with zero human code.

It's called OpenDevin, and here's what it actually does:

1. Reads a GitHub Issue labeled "agent"
2. Classifies the task domain (backend, frontend, database, AI, mixed)
3. Routes to a specialized agent
4. Executes 4 cognitive phases — Scan, Investigate, Draft Plan, Build — each validated by an independent AI Judge that can reject and force a redo
5. Validates everything inside an isolated Docker container (syntax, imports, tests, security scan, lint)
6. Opens a PR, monitors CI, auto-fixes failures from real GitHub Actions logs
7. Auto-merges if all gates pass. Escalates to human review if it doesn't converge.

The pipeline has 13 nodes, 5 quality layers, 17 typed failure categories with specialized fix prompts, and a 2-layer repair loop (pre-commit + post-CI).

Real execution: 8 backend issues processed in 36 minutes. 7 auto-merged. 1 escalated. 87.5% success rate. No manual intervention on the 7 that passed.

This is not a wrapper around an LLM that generates code and hopes for the best. Every phase has a gate. Every gate has a judge. Every failure is classified and routed to a specialized repair strategy. The system doesn't guess — it validates, and if it can't fix something, it says so.

Stack: LangGraph (state machine), OpenRouter (DeepSeek v3 for generation, Gemini Flash for judge, Claude as fallback), Docker for isolated validation, Bandit + Semgrep for security, ChromaDB for RAG, GitHub Actions for CI/CD.

Is it production-ready? No. It's an advanced POC. Known limitations: single-threaded, generates full files instead of surgical edits, no public benchmark yet. I'm honest about that because I think the engineering community deserves honesty over hype.

But the process engineering is real. Typed failure classification, 14-pass pre-commit sanitization, incremental regression detection, convergence monitoring on repair loops — these are patterns I haven't seen in most commercial AI coding tools.

Live site with full architecture and real execution data:
https://ricardobnjunior.github.io/opendevin-site/

Architecture deep dive:
https://ricardobnjunior.github.io/opendevin-site/architecture.html

Open for conversations about autonomous code systems, AI engineering, and what it takes to make LLM-generated code actually reliable.

#AIEngineering #AutonomousCoding #LLM #SoftwareEngineering #OpenSource #DevTools #LangGraph

---

## Image Prompt

Generate a dark-themed technical hero image for a LinkedIn post about an autonomous code pipeline system called "OpenDevin".

**Visual concept:** A sleek, minimalist flowchart/pipeline visualization on a dark navy background (#0a0a1a). The pipeline flows top-to-bottom with 4 glowing nodes representing cognitive phases: Scan (cyan), Investigate (purple), Draft Plan (violet), Build (green). Between each node, a small orange diamond represents an "AI Judge" gate. Below the 4 phases, a quality assurance section with validation nodes. At the bottom, a green "Auto-Merge" endpoint glows brightly.

**Style:** Clean, geometric, developer-aesthetic. Similar to a Mermaid diagram but rendered as polished graphic design. Subtle radial gradient glow behind the pipeline. No text except the phase names on the nodes. Neon accent lines connecting nodes (#e94560 red for connections). Dark card-style backgrounds for each node (#12122a). The overall feel should be: "serious engineering, not startup hype".

**Aspect ratio:** 1200x628 (LinkedIn recommended)

**Color palette:**
- Background: #0a0a1a (near-black navy)
- Accent: #e94560 (red-pink for connections)
- Scan node: #0ea5e9 (cyan)
- Investigate node: #8b5cf6 (purple)
- Draft Plan node: #a855f7 (violet)
- Build node: #22c55e (green)
- Judge diamonds: #f97316 (orange)
- Quality nodes: #0ea5e9 (cyan)
- Output node: #10b981 (emerald green, glowing)

**Do not include:** logos, stock photos, people, emojis, excessive text, gradients that look cheap, 3D effects, or anything that looks like a marketing template.
