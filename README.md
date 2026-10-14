# PlantUML Project Template

## 概要

PlantUMLを使った設計資料を作成するためのテンプレートです。オンラインストアを例に、クラス図、ER図、シーケンス図のソースと生成済みSVGを配置しています。
PlantUMLによる設計ドキュメントを管理するプロジェクトや、設計資料を含むアプリケーションプロジェクトの初期構成として利用できます。サンプルの業務ドメインや図は、対象プロジェクトに合わせて置き換えてください。

## 主な機能

- **Dev Container**: Ubuntuベースの開発コンテナを利用できます。
- **PlantUML**: Java、PlantUML、Graphvizをコンテナにインストールし、ローカルレンダリングに対応しています。
- **VS Code連携**: PlantUML、Markdownプレビュー、Markdown整形・lint用の拡張機能を利用できます。
- **図のソース管理**: `.puml`ファイルと、出力したSVGファイルを分離して管理できます。

## 前提条件

以下をホスト環境に用意してください。

- Git
- Docker DesktopまたはDocker Engine
- Visual Studio Code
- VS CodeのDev Containers拡張機能

## 使用方法

1. GitHubで本テンプレートの **Use this template** を選択します。
2. 新しいリポジトリ名と公開範囲を設定し、リポジトリを作成します。
3. 作成したリポジトリをクローンします。

   ```bash
   git clone https://github.com/<ユーザー名>/<リポジトリ名>.git
   cd <リポジトリ名>
   ```

4. VS Codeでフォルダーを開き、コマンドパレットから **Dev Containers: Reopen in Container** を実行します。
5. `uml/`のサンプルを編集し、PlantUML拡張機能で図をプレビュー・出力します。
6. `docs/`に設計資料を作成し、必要な画像を`images/`へ保存します。

## ディレクトリ構成

```text
.
├── .devcontainer/
│   ├── Dockerfile          # PlantUML、Java、Graphvizを含む開発コンテナ
│   └── devcontainer.json   # Dev ContainerとVS Code拡張機能の設定
├── .github/
│   ├── instructions/       # Python・ドキュメント向けの作業指針
│   └── ...                 # Issue/PRテンプレートなど
├── docs/
│   └── sample-document.md  # 生成図を使った設計資料のサンプル
├── images/
│   └── uml/                # PlantUMLから出力したSVG画像
├── uml/
│   ├── class/              # クラス図のソース
│   ├── er/                 # ER図のソース
│   └── sequence/           # シーケンス図のソース
└── README.md
```

## 開発手順

### コンテナを起動する

1. VS Codeでプロジェクトを開きます。
2. **Dev Containers: Reopen in Container** を実行します。
3. `.devcontainer/Dockerfile`の変更後は、**Dev Containers: Rebuild Container** を実行します。

### PlantUMLの図を生成する

設定済みの出力形式はSVGで、出力先は`images/`です。

#### PlantUML拡張機能のエクスポート機能を使用する場合

1. 対象の`.puml`ファイルを開きます。
2. `Ctrl+Shift+P`でコマンドパレットを開きます。
3. `PlantUML: Export Current Diagram`を選択します。

#### コマンドラインから実行する場合

```bash
plantuml -tsvg -o /workspaces/<リポジトリ名>/images uml/**/*.puml
```

## カスタマイズ方法

### 図を追加・変更する

1. 用途ごとに`uml/`配下へ`.puml`ファイルを追加します。
2. PlantUMLでSVGを生成し、対応する`images/uml/`配下へ保存します。
3. `docs/`のMarkdownから相対パスで画像を参照します。
