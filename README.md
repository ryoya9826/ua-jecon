# ua-jecon

An extended BibTeX style for economics (`ua-jecon.bst`) and its wrapper package (`ua-jecon.sty`).

- Author / Maintainer: Ryoya Ando — <https://ryoya9826.github.io/>
- Version: 0.7.1 (2026-11-16)
- License: LaTeX Project Public License (LPPL), version 1.3c or later
- Repository: <https://github.com/ryoya9826/ua-jecon>

## Description (English)

`ua-jecon.bst` is a derived work of `jecon.bst` (v6.2.1) by Shiro Takeda
(<https://github.com/ShiroTakeda/jecon-bst>), a BibTeX style for economics
that handles both Japanese and English references. It adds:

- new fields `arxiv`, `etranslator` and `label`;
- automatic `a`, `b`, ... suffixes for entries with the same author(s) and year;
- amsrefs-like compressed labels (e.g. `[And26]`) written to the `.aux` file.

`ua-jecon.sty` loads `natbib`, selects `\bibliographystyle{ua-jecon}` and
defines `\acite{key}` (and `\acite{key}*{note}`), which prints the compressed
label. Do not call `\bibliographystyle` again in your document.

Requirements: upLaTeX + upBibTeX, or LuaLaTeX with upBibTeX (for Japanese entries).
The documentation (`ua-jecon-doc.pdf`) is written in Japanese.

### Files

| File | Description |
| --- | --- |
| `ua-jecon.sty` | Wrapper package |
| `ua-jecon.bst` | BibTeX style |
| `ua-jecon-doc.tex`, `ua-jecon-doc.pdf` | Documentation (Japanese) and its source |
| `ua-jecon-example.bib` | Sample database used by the documentation |
| `README.md` | This file |

To rebuild the documentation:

```
uplatex ua-jecon-doc
upbibtex ua-jecon-doc
uplatex ua-jecon-doc
uplatex ua-jecon-doc
dvipdfmx ua-jecon-doc
```

### License

This material is subject to the LaTeX Project Public License, version 1.3c
or later. The work has the LPPL maintenance status `maintained`; the Current
Maintainer is Ryoya Ando. As required by the LPPL, `ua-jecon.bst` is renamed
from `jecon.bst` and its changes are listed in the file header.

---

# ua-jecon パッケージ（日本語）


Author: Ryoya Ando — [https://ryoya9826.github.io/](https://ryoya9826.github.io/)  
License: [LPPL](https://www.latex-project.org/lppl.txt) version 1.3c 以降  

`ua-jecon.bst` は，武田史郎氏によって作成された経済学用 BibTeX スタイルファイル [`jecon.bst`](https://github.com/ShiroTakeda/jecon-bst) (v 6.2.1) をベースに，独自の拡張を加えた派生版です．
`ua-jecon.sty`は，そちらを利用しやすくするためのパッケージです．


## ベースとなったオリジナル作品

- プロジェクト名: `jecon.bst` (経済学用 BibTeX スタイルファイル)
- 原著作者: 武田史郎 (Shiro Takeda)
- 配布元: [https://github.com/ShiroTakeda/jecon-bst](https://github.com/ShiroTakeda/jecon-bst)
- バージョン: v 6.2.1

## 主な特徴・拡張内容

1. ベース: `jecon.bst` v 6.2.1
2. 新規フィールドの追加:
  - `arxiv`: arXiv のプレプリント情報を扱うためのフィールドを追加.
  - `etranslator`: 翻訳者情報の追加フィールド（英語・日本語など複数言語対応時）．
  - `label`: ユーザー定義の引用ラベル．
3. 重複エントリへの添字付与:
  - 同一著者・同一年による重複エントリに対して，`a, b` などの接尾辞（`extra.label`）を自動的に付与します．
4. `amsrefs` への対応:
  - `amsrefs` パッケージに近い形式での整形に対応し，`.aux` ファイルに情報を書き出します．
5. その他のカスタマイズ:
  - `bysame = #0`
  - `authorname = #2`
  - `number.index = #1`
  - `unicode = #1`
  - `bst.number.index` や `bibhang` 等の出力レイアウト微調整．

## 動作条件


| 項目       | 条件                                       |
| -------- | ---------------------------------------- |
| ベース      | `jecon.bst` v 6.2.1                      |
| TeX エンジン | upLaTeX + upBibTeX または LuaLaTeX           |
| パッケージ構成  | `ua-jecon.sty` が内部で `natbib` 等を自動的に読み込みます |


## ライセンス

元制作物である `jecon.bst` と同様に，LaTeX Project Public License (LPPL) version 1.3 以降が適用されます．

## 使用方法

プリアンブルで `ua-jecon` パッケージを読み込むだけで、必要な設定（`natbib`の読み込み、`\acite`コマンドの定義、`\bibliographystyle{ua-jecon}`の指定）がすべて完了します。`\bibliographystyle` を文書中で再度指定しないでください。

```latex
\documentclass{article}
% プリアンブルでパッケージを読み込むだけ
\usepackage{ua-jecon}

\begin{document}
Citing a reference in the text: \cite{example_key}, \acite{example_key}.

\bibliography{refs} % あなたの .bib ファイル（サンプルは ua-jecon-example.bib）
\end{document}
```

> Note: `.bib` ファイルの具体的な書き方（日本語著者名のフォーマットや特殊なフィールドの使い方など）に関する細かな要件は，ベースとなった[オリジナルの `jecon.bst` のドキュメント（`jecon-example.pdf` 等）](https://github.com/ShiroTakeda/jecon-bst)をご参照ください．

詳細な仕様や出力例については，`ua-jecon-doc.tex`（およびコンパイル後の PDF）をご参照ください．

本文では，`natbib` 標準の `\cite` に加え、`amsrefs`風の圧縮ラベル（例：`[And26]`）を出力する `\acite` が利用できます（`\acite{キー}*{Thm.~1}` で追記も可能）。圧縮ラベルは自動生成されて `.aux` に書き込まれるため、ユーザーが手動でラベル定義をする必要はありません。

---

## 変更履歴

- Version 0.7.1 (2026-11-16): `\acite` の直前に余分な空白が入る不具合を修正．未定義ラベルの警告を追加．CTAN 公開に向けたライセンス表記の整備．サンプル文献ファイルを `ua-jecon-example.bib` に改名．
- Version 0.7 (2026-04-21): 重複エントリへの `a,b` 付与，`label` フィールドの追加，`number.index` フォーマットの調整．パッケージとして提供 (`ua-jecon.sty`)．
- Version 0.6 (2026-04-07): `ua-jecon.version` 変数の修正，`\harvarditem` コメントの typo 修正．
- Version 0.5 (2021-12-20): `amsrefs` 形式に整形したデータを `.aux` に書き出し．
- Version 0.4 (2021-08-25): `etranslator` フィールドを追加．
- Version 0.3 (2021-08-05): `bst.amsrefs` を追加し，`amsrefs` 形式の出力に対応．
- Version 0.2: ベースを `jecon.bst` v6.2.1 に更新．
- Version 0.1: `arxiv` フィールドを追加．
