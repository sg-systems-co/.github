# SG Systems

Consulting and forward-deployed engineering for applied AI in Southeast Asia.
We embed with enterprises and the systems integrators that serve them, and
build, ship, and operate what they need — compliant, locally tuned, and                                                                                                                                                                                               
running where the data lives.

Singapore ·
[sg-systems.co](https://www.sg-systems.co) ·
[Hugging Face](https://huggingface.co/sgsystems) ·
[LinkedIn](https://www.linkedin.com/company/sg-systems-pte-ltd) ·
[sebastian@sg-systems.co](mailto:sebastian@sg-systems.co)

## Open source: a 7B hybrid on a laptop

Our public work is on running hybrid Mamba-2 models on Apple Silicon inside
the memory a phone or laptop actually gives you. `Falcon-H1-7B-Instruct` goes
from 15.5 GB to 3.48 GB and runs at **~75 tok/s decode, ~1940 tok/s prefill,
in 3.73 GB resident** — without losing factual recall.

Edge inference is two separate constraints, so there are two tools:

| Repository | Constraint | What it does |
|---|---|---|
| [`forge`](https://github.com/sg-systems-co/forge) | Capacity | Training-free ternary (1.58-bit) post-training quantization. Emits stock GGUF on llama.cpp's `TQ2_0` block type, so checkpoints load on unmodified llama.cpp — no custom kernel, no forked runtime. MIT. |
| [`helix`](https://github.com/sg-systems-co/helix) | Bandwidth | Chunk-parallel SSD (`SSM_SCAN`) Metal kernel for state-space models, as a drop-in ggml custom operator. Chunk-state GEMM on the matrix unit; bf16 through the M5 Neural Accelerators via MPP. |
| [`forge-helix`](https://github.com/sg-systems-co/forge-helix) | — | The overview and release tooling for the pair: the physics, the benchmarks, and the 42-line llama.cpp patch. **Start here.** |
| [`helix-chat-ui`](https://github.com/sg-systems-co/helix-chat-ui) | — | Native SwiftUI chat client running the quantized model on the HELIX-accelerated engine. |

The shipping checkpoint is on Hugging Face:
[`sgsystems/Falcon-H1-7B-FORGE-v2`](https://huggingface.co/sgsystems/Falcon-H1-7B-FORGE-v2)
— 2.06 bpw average, 12/12 on the factual-recall probe, loads on stock llama.cpp.

## Products

- [**AnswerRank**](https://answerrank.app) — answer-engine optimisation. Track
  how ChatGPT, Claude, Perplexity, and Gemini talk about your brand.

## Working with us

We deliver one operational outcome at a time on a three-layer engine —
orchestration with audit trails and human-in-the-loop gates, localized
ingestion for Thai, Bahasa, Malay, Vietnamese, and Tagalog inputs (text,
voice, slips, documents), and action connectors into regional rails (LINE OA,
WhatsApp Business, PromptPay, Flash Express, SAP, Salesforce).

Engagements run as a short [Discovery](https://www.sg-systems.co/services/),
an 8–12 week Implementation, or an embedded quarterly retainer for SI partners.
Details and pricing are on the [services page](https://www.sg-systems.co/services/);
technical notes and model releases land on [/research](https://www.sg-systems.co/research/).

→ [Start a conversation](https://www.sg-systems.co/contact/)
