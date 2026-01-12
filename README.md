# 🌈 OSS Contribution Graph

複数のOSSプロジェクトへの貢献を色分けして1つのグラフに表示するツールです。
GitHub Profile READMEに貼り付けるだけで使えます。

## 📸 プレビュー

![OSS Contribution Graph](https://your-deployment.vercel.app/api/graph?username=yujiteshima&orgs=rails:CC0000:Rails,hotwired:1a1a1a:Hotwire&months=6)

## 🚀 使い方

### 1. デプロイ

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/yourusername/oss-contribution-graph)

### 2. 環境変数を設定

Vercelのダッシュボードで以下の環境変数を設定:

| 変数名 | 説明 |
|--------|------|
| `GITHUB_TOKEN` | GitHub Personal Access Token (read:user スコープ) |

### 3. README.mdに貼り付け

```markdown
![OSS Contributions](https://your-deployment.vercel.app/api/graph?username=YOUR_USERNAME&orgs=rails:CC0000:Rails,hotwired:1a1a1a:Hotwire&months=6)
```

## 📝 パラメータ

| パラメータ | 説明 | デフォルト | 例 |
|-----------|------|-----------|-----|
| `username` | GitHubユーザー名 | `yujiteshima` | `yujiteshima` |
| `orgs` | 組織設定 (カンマ区切り) | rails, hotwired | `rails:CC0000:Rails,hotwired:1a1a1a:Hotwire` |
| `months` | 表示期間 (1-12) | `6` | `3`, `6`, `12` |
| `demo` | デモモード | `false` | `true` |

### orgs パラメータの形式

```
組織名:色(6桁HEX):ラベル
```

例:
- `rails:CC0000:Rails` → railsの貢献を赤色で表示、ラベルは「Rails」
- `hotwired:1a1a1a:Hotwire` → hotwiredの貢献を黒色で表示
- `honojs:E36002:Hono` → honojsの貢献をオレンジで表示

## 🎨 カスタマイズ例

### Rails + Hotwire + Hono

```markdown
![OSS Contributions](https://your-app.vercel.app/api/graph?username=yujiteshima&orgs=rails:CC0000:Rails,hotwired:1a1a1a:Hotwire,honojs:E36002:Hono&months=6)
```

### 3ヶ月表示

```markdown
![OSS Contributions](https://your-app.vercel.app/api/graph?username=yujiteshima&orgs=rails:CC0000:Rails&months=3)
```

### デモモード（トークンなしで動作確認）

```markdown
![OSS Contributions](https://your-app.vercel.app/api/graph?username=yujiteshima&demo=true)
```

## 🔧 ローカル開発

```bash
# 依存関係をインストール
npm install

# 環境変数を設定
export GITHUB_TOKEN=your_github_token

# 開発サーバーを起動
npm run dev
```

## 📋 必要なGitHub Token スコープ

- `read:user` - ユーザー情報の読み取り
- `read:org` - 組織情報の読み取り（組織IDの取得に必要）

## 🔗 仕組み

1. GitHub GraphQL APIで組織IDを取得
2. `contributionsCollection(organizationID: $orgId)` で組織ごとの貢献をフィルタリング
3. 複数組織のデータをマージ
4. SVG画像として出力

## 📄 ライセンス

MIT

## 🙏 クレジット

Inspired by:
- [github-readme-stats](https://github.com/anuraghazra/github-readme-stats)
- [github-readme-activity-graph](https://github.com/Ashutosh00710/github-readme-activity-graph)
