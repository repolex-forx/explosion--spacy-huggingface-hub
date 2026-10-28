# Repolex Knowledge Graph of explosion/spacy-huggingface-hub

RDF knowledge graph data for [explosion/spacy-huggingface-hub](https://github.com/explosion/spacy-huggingface-hub), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download explosion/spacy-huggingface-hub
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 1e27b866ff8a92d5c9601fc2bf483b25a4f4ef15
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 1e27b866ff8a92d5c9601fc2bf483b25a4f4ef15
│           └── chunk-001.nq.gz
├── blob
│   ├── 038e0b5dea18f6be1c89c49e877a8d92ecb6863b.nq.gz
│   ├── 2518fcee855ef2ed499faceb947651a25ff800da.nq.gz
│   ├── 2b1bb09818e08cf4923c4888a7187a68c2ca8c00.nq.gz
│   ├── 30478fb55d22093f61fa91aaf4b163bd64b8cfbd.nq.gz
│   ├── 3583a2b2eaea1e8357acaa1a6231273836992bc9.nq.gz
│   ├── 408ab542bc92e487bbe44b327080b4024a4cde2c.nq.gz
│   ├── 913f4b7188b9e27a76ca88651a3f04ba065a15d5.nq.gz
│   ├── a4d7220f6ace584c148ca45f30093ac88155b2c3.nq.gz
│   └── c1a7121c1bd6c9648bc686c95b1c7a94dd69cdd3.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 1e27b866ff8a92d5c9601fc2bf483b25a4f4ef15.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 17 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[explosion/spacy-huggingface-hub](https://github.com/explosion/spacy-huggingface-hub)

---
*Parsed on 2026-10-28 by [repolex](https://repolex.ai)*
