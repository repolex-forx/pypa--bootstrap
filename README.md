# Repolex Knowledge Graph of pypa/bootstrap

RDF knowledge graph data for [pypa/bootstrap](https://github.com/pypa/bootstrap), parsed by [repolex](https://repolex.ai).

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
rlex download pypa/bootstrap
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 9797ac6a7324041beee7e37d232aa76c733e89b3
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 9797ac6a7324041beee7e37d232aa76c733e89b3
│           └── chunk-001.nq.gz
├── blob
│   ├── 0bf02958398aa3cbf8d574f9594e0047ebf31972.nq.gz
│   ├── 19e70f6ba5a5cd3edde066d9626d84668a7be44d.nq.gz
│   ├── 1dd3bad4768293313684a0112f231481cb57b284.nq.gz
│   ├── 37bb7a6d9271e3b3d33602968ea3d47445ca8138.nq.gz
│   ├── 4061ad41487def9e9d08ca2312e7f8724e34201f.nq.gz
│   ├── 5d01601c29dbbf3d8e2f74313341e1c90020151f.nq.gz
│   ├── 68177aca1dd268c25ed9354a24cf2943f4ce5daf.nq.gz
│   ├── 730fd9b963a6f84322cba029a2772cb85ce29c68.nq.gz
│   ├── 7f07619626e802220fe8ca8b1c98f0221aaa4ec6.nq.gz
│   ├── 9219ab776d76ab939f763b753ad357e269681e98.nq.gz
│   ├── a50d166c12fcb855700d12363e5c286fc6ec0ab7.nq.gz
│   ├── ce9df8b69ffca020f0fec2697192d7cb98fda78c.nq.gz
│   ├── e35015771f342e1e463b9200c686f6746d891073.nq.gz
│   └── f2c373bc2540191eb308ee3ae09a167a7087f6c3.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 9797ac6a7324041beee7e37d232aa76c733e89b3.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 22 files
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

[pypa/bootstrap](https://github.com/pypa/bootstrap)

---
*Parsed on 2026-10-11 by [repolex](https://repolex.ai)*
