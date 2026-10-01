# Repolex Knowledge Graph of block/aittributor

RDF knowledge graph data for [block/aittributor](https://github.com/block/aittributor), parsed by [repolex](https://repolex.ai).

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
rlex download block/aittributor
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── d5e38cb77b428828982e24b27d43ce9e6295be78
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── d5e38cb77b428828982e24b27d43ce9e6295be78.nq.gz
│   └── repolex
│       └── d5e38cb77b428828982e24b27d43ce9e6295be78
│           └── chunk-001.nq.gz
├── blob
│   ├── 02cb8fcb5372748d4273b6a49eceb78fbdb15ce6.nq.gz
│   ├── 0367d2331a2cbfb3dadb43da08affe106a235c28.nq.gz
│   ├── 0ba9db25329d0b336e39ca8cde8470c5b7bc45eb.nq.gz
│   ├── 0bcaa70cae4090a720428d146bcbed485e49d4d2.nq.gz
│   ├── 1419f77545175d5b68ce9550983a7e2b3cc438ff.nq.gz
│   ├── 1dc9a8cbb1d50b96940e03fd10df302b02e3b858.nq.gz
│   ├── 1ec22601d4fa297ed1ee444e65c2d4aed1ab7028.nq.gz
│   ├── 22a4df98f7f4c156258f4e1156a75e8618d44a71.nq.gz
│   ├── 25f0bc5ed80683a81f46e6bfd1cf8ea0b56c6807.nq.gz
│   ├── 31559b7d115e3c105b328cce9b9dcd9774025061.nq.gz
│   ├── 383f4511d444516caed0fd113ee8a2b640cd2290.nq.gz
│   ├── 47dc3e3d863cfb5727b87d785d09abf9743c0a72.nq.gz
│   ├── 51e1685dc1f6fa65d4debfcda8c817038b0906fa.nq.gz
│   ├── 69e96b8e33dbdd2f7131d876cd027d450be30f4e.nq.gz
│   ├── 6bccf43368fd7c96d9c659562a5142b8b8cb98a1.nq.gz
│   ├── 6c025bc563895062e8e9558416c1926d60ee2245.nq.gz
│   ├── 729111d5741f58b91d9b9ed643aa6962c1320c1e.nq.gz
│   ├── 75306517965a54731b94dca8bace640e856af115.nq.gz
│   ├── 7c2ee9b5ee0b69389214db6e571318aaad7fa2e2.nq.gz
│   ├── 816066f4755caecbea428ebfe33fecd477e0bb7e.nq.gz
│   ├── 862ee3c28647e7a58801a75236855c269c1448ae.nq.gz
│   ├── 8a16a4cc79b69cfc15fdcf1b8d2df0b72fe99d8a.nq.gz
│   ├── 8c53935c11e7cf631ff708def484ded15c745450.nq.gz
│   ├── 906ee94ca6891416a56b8a1df9e0bbcc0000429d.nq.gz
│   ├── 9582fc588754f78d9875691a3bd5e674295436b3.nq.gz
│   ├── a421c5e6d174ec6311a25a8f2b0eb7744d706513.nq.gz
│   ├── c00d2e22d50c9929c54a2d20280c1394ccddf99c.nq.gz
│   ├── cbc3cd5c2d65534351aac833aff817c836e94a9a.nq.gz
│   ├── e78d7326edc55253bbe27064a5a306bc66923734.nq.gz
│   ├── e889550ba4cbc92a720527042e5f6e7a303bfcbc.nq.gz
│   ├── eb409899533e56dcac7488146f113b6f028ccddf.nq.gz
│   ├── f8803abcbd09d8d45884e9c6a3f09570c3963b88.nq.gz
│   ├── fa0376db0ff9e4d830c155562e670e98339061e9.nq.gz
│   ├── fb6d193b736e9328861731e2583ac518d06b928f.nq.gz
│   ├── fe0867819936afc4af0bf1512d453bc7465e7db2.nq.gz
│   └── fe28214d3352b0ed40820a4999317694c8b1ef57.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── d5e38cb77b428828982e24b27d43ce9e6295be78.nq.gz
├── filetree
│   └── d5e38cb77b428828982e24b27d43ce9e6295be78.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

15 directories, 46 files
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

[block/aittributor](https://github.com/block/aittributor)

---
*Parsed on 2026-10-01 by [repolex](https://repolex.ai)*
