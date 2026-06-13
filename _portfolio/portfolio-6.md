---
title: "Compute-Skipping Policies for Diffusion LLMs (dLLM-v2) (2026)"
collection: portfolio
year: 2026
order: 1
excerpt: "Two compute-skipping policies for diffusion LLMs (Fast-dLLM v2) that reuse stable hidden states across denoising steps to cut FLOPs: a layer-level cache-reuse policy and a stability-aware token-level policy that recomputes only the least-similar tokens.<br/><a href='/files/dLLM_v2_compute_skipping.pdf'>Report (PDF)</a><br/><img class='portfolio-thumb' src='/images/dllm-compute-skipping.png' alt='Compute-skipping reuse across transformer blocks in dLLM-v2'>"
---

Built on the Fast‑dLLM v2 codebase, this project implements and analyzes two ways to skip
redundant computation across denoising steps:

- **Layer-level skipping** — cache each decoder layer's input hidden states and output, then
  reuse the cached output on the next step when the new input is highly cosine‑similar.
- **Token-level skipping** — a finer‑grained, stability‑aware policy that recomputes only the
  least‑similar tokens per layer (using an adaptive reuse ratio driven by the batch‑average
  cosine similarity) and reuses cached outputs for the rest.

The write‑up studies the resulting accuracy‑vs‑FLOPs trade‑off — how much computation can be
safely skipped before generation quality degrades.

Report: <a href="/files/dLLM_v2_compute_skipping.pdf">Implementation of Two Compute-Skipping Policies in dLLM-v2 (PDF)</a>
