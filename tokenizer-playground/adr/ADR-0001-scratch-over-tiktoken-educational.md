# ADR-0001: Implement BPE from scratch over tiktoken's educational module

## Status
Accepted

## Context
tiktoken ships a built-in educational submodule
(`from tiktoken._educational import SimpleBytePairEncoding`)
that already implements BPE for learning purposes.
The goal of this project was to understand tokenization
deeply enough to explain it in a production system.

## Decision
Implement both character-level and BPE tokenizers from scratch
using only Python + numpy.

## Alternatives Considered
- **tiktoken educational module** — rejected because it abstracts
  the merge loop away; you run it without seeing the algorithm.
- **HuggingFace tokenizers library** — rejected, too high-level
  for learning purposes.

## Consequences
- Easier: full visibility into every step of the merge loop;
  can modify and experiment freely.
- Harder: no production use; won't handle Unicode or
  special tokens correctly.
- Insight gained: BPE discovers "th", "the", "ing" purely
  from frequency — no linguistic knowledge encoded.
