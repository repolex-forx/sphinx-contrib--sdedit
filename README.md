# Repolex Knowledge Graph of sphinx-contrib/sdedit

RDF knowledge graph data for [sphinx-contrib/sdedit](https://github.com/sphinx-contrib/sdedit), parsed by [repolex](https://repolex.ai).

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
rlex download sphinx-contrib/sdedit
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 0f8da02c72bdf9e82a8b323cb2d372244993659d
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 0f8da02c72bdf9e82a8b323cb2d372244993659d
│           └── chunk-001.nq.gz
├── blob
│   ├── 1acac3eb41d3dcaba0a5ba6411a502f6b43dab4e.nq.gz
│   ├── 211a6c66d816ff6c93eb8017dcbadeee707ca4f7.nq.gz
│   ├── 2d74c58f248790e34e482eb07e20ec6c753c9d2d.nq.gz
│   ├── 2eba9160d403563d8b100534a4d950281de057e6.nq.gz
│   ├── 37467bdc4752a31da7763d7cf24051ab5a8a4307.nq.gz
│   ├── 4cbc2f9b57e4498d5cd07551d675a3ad7fb23697.nq.gz
│   ├── 6a5857faa3e7a0f1c0fdf983379b584348c97743.nq.gz
│   ├── 821bf26266b164f22eb45c5465ab22e0c66db943.nq.gz
│   ├── 8cd3a3544d734aa93dd9b311221ff0d8536b1c9d.nq.gz
│   ├── b184c255fd4b9e85fe255782923d2bfd2e083ee1.nq.gz
│   ├── b5a7dc29ef0f7f3593b1c61cfc5dfe8a17d3918c.nq.gz
│   └── d4693d9e53b2e1c1def205eb48984325fe24a918.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 0f8da02c72bdf9e82a8b323cb2d372244993659d.nq.gz
└── tag
    └── tag.nq.gz

11 directories, 18 files
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

[sphinx-contrib/sdedit](https://github.com/sphinx-contrib/sdedit)

---
*Parsed on 2026-11-07 by [repolex](https://repolex.ai)*
