# Repolex Knowledge Graph of karpathy/minGPT

RDF knowledge graph data for [karpathy/minGPT](https://github.com/karpathy/minGPT), parsed by [repolex](https://repolex.ai).

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
rlex download karpathy/minGPT
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 37baab71b9abea1b76ab957409a1cc2fbfba8a26
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 37baab71b9abea1b76ab957409a1cc2fbfba8a26
│           └── chunk-001.nq.gz
├── blob
│   ├── 00d8def32b5f0bdee5e42841def7ef8ca148caee.nq.gz
│   ├── 3d89960112452062baf36bb13d43a92028fc0f0e.nq.gz
│   ├── 432505d23197589261fec9f65f7cf522283f87e4.nq.gz
│   ├── 4e74622e7567131b81ab9b515ad2bd43d79423fc.nq.gz
│   ├── 55f03ee1caf4290e86f5ce02570553a87caeee23.nq.gz
│   ├── 5de925b06f4d6062a289cb24fe945e0f8a2119db.nq.gz
│   ├── 8070bcb841210296a6c5f29b4ecb51d4a408e51f.nq.gz
│   ├── 83ee22dc07707fd9cb62eb3215c1c1e4b150b5c9.nq.gz
│   ├── 9a2d64f6f630c1a50ea7a48fbb13663901827d5e.nq.gz
│   ├── 9bc9d7f75a0b6aa3744f5233332dfa45aaa2deda.nq.gz
│   ├── 9debd1773a92dda866918ce8d8e0d32fb0692889.nq.gz
│   ├── ad168f43935ce593a9dc1d4bd3f66ec901b58cf1.nq.gz
│   ├── af864ecbd61b73659731b2cc762802fce097a981.nq.gz
│   ├── b8468ef9341aeb6fd76a6085c04a9909c9eaede0.nq.gz
│   ├── c0d085210a8f438bbea28be5e103c67e39fd0be9.nq.gz
│   ├── dab52a8280d865d9e959e06639289db2ebef0361.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── f92cfd2278fd261651989b4653b75203ef5f58cb.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 37baab71b9abea1b76ab957409a1cc2fbfba8a26.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 26 files
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

[karpathy/minGPT](https://github.com/karpathy/minGPT)

---
*Parsed on 2026-10-17 by [repolex](https://repolex.ai)*
