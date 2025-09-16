# INVADERS NEO

> 単一HTMLファイルで動く、インベーダー風ミニゲーム。ガラス×ネオンのミニマルUI、キーボード＆タッチ対応、レティナ対応。

![screenshot placeholder](docs/screenshot-01.png)

---

## ✨ TL;DR（すぐ遊ぶ）

1. このリポジトリをクローン or ZIPでダウンロード。
2. `index.html` をブラウザで開く（ダブルクリックでOK）。
3. VS Code ユーザーは拡張機能 **Live Server** を入れて `index.html` を右クリック → **Open with Live Server** 推奨。

> **デモURL**: （デプロイしたらここにGitHub Pages/Netlify等のURLを入れてください）

---

## 🎮 ゲームの目的

短時間で **撃つ→避ける→集中** を楽しめるミニゲーム。全滅で **Wave（難度）アップ**。スコア更新をめざそう！

---

## 🧩 主な機能

* スコア / ライフ / ウェーブ表示（HUD）
* 難易度切替：**やさしい / ふつう / むずかしい**
* **サウンドON/OFF**（軽量ビープ音）
* **ポーズ（P）** / **リスタート（R）**
* **キーボード & タッチ**操作（モバイル対応）
* **高DPI（Retina）対応** / レスポンシブ
* 練習用の **当たり判定ガイド**

---

## ⌨️ 操作方法

* 移動：**←→** または **A / D**
* ショット：**スペース**
* ポーズ：**P**（トグル）
* リスタート：**R**
* モバイル：画面下の **◀︎ / ● / ▶︎** ボタン

---

## 📁 ファイル構成

```
.
├── index.html            # 単一ファイル（HTML/CSS/JS 内蔵）
└── docs/
    ├── screenshot-01.png # README用スクショ（任意）
    └── screenshot-02.png
```

> 最低限は `index.html` だけで動作します。`docs/` はREADME装飾用の例です。

---

## 🏗 開発/編集（VS Code）

1. VS Code を開く → このフォルダを **Open Folder**。
2. 拡張 **Live Server** を入れる（推奨）。
3. `index.html` を開いて編集。保存するとブラウザが自動更新されます。

---

## ⚙️ カスタマイズのヒント

**色変更**：`<style>` の `:root` 変数を編集。

```css
:root{
  --acc1:#7cf1ff; /* メインアクセント */
  --acc2:#ff8bd1; /* サブアクセント */
}
```

**自機デザイン**：`drawShip()` 関数内の図形サイズを調整。

**効果音**：`beep(freq, dur, type, vol)` の引数を変更（`type`: `sine`/`square`/`triangle`/`sawtooth`）。

**難易度チューニング**：`reset()` / `enemyShootTimer` の式や `speed` を調整。

---

## 🧪 テスト（内蔵の簡易チェック）

`index.html` には軽量テストを同梱しています。ブラウザの **DevTools → Console** を開いて、`TEST ...` の **assert** がエラーなく通ることを確認してください。

### どんなテスト？

* `clamp()` の境界/中間値
* `hit()`（矩形×円の当たり判定）の真偽
* 敵生成（初期Wave）のカウント整合
* `beep` 定義の存在チェック

### 手動チェック・チェックリスト

* [ ] PCのキーボードで操作できる（←→/A/D/Space/P/R）
* [ ] モバイルのタッチボタンで操作できる（◀︎/●/▶︎）
* [ ] 難易度ごとに敵スピード／弾頻度が変わる
* [ ] 当たり判定ガイドONで枠が表示される
* [ ] Waveクリアで次Waveへ遷移しスコアが加算
* [ ] Game Over後にメニューへ戻れる

> さらに自動化したい場合は、関数をモジュール化して **Jest** 等へ切り出す構成に拡張してください（本作は1ファイル完結を優先）。

---

## 🧑‍🦽 アクセシビリティ

* `<canvas>` に `aria-label` を付与
* 操作説明文をメニューに明記
* ALTテキスト例（X/Twitter用）

  * 「ネオンの発光とガラス風UIのゲーム画面。下部にプレイヤー機、上部にエイリアン隊列。左上にHUD（SCORE/LIVES/WAVE）。」

---

## 🚀 デプロイ（例）

### GitHub Pages

1. GitHubにリポジトリを作成→ `index.html` をプッシュ
2. **Settings → Pages** を開く
3. **Source** を `main`（または `docs`）に設定
4. 公開URLが発行されます（少し待つとアクセス可能）

### Netlify / Vercel

* 新規プロジェクト作成 → リポジトリを選択 → ビルド不要（静的） → デプロイ

---

## 🛠 トラブルシュート

* **音が鳴らない**：ブラウザはユーザー操作前の自動再生を制限します。**Start** ボタンから開始すると鳴ります。
* **ぼやける**：ウィンドウリサイズで解消する場合があります（HiDPIスケーリング調整）。
* **キーが効かない**：IME（日本語入力）がONだとスペースが効きにくいことがあります。OFFで試してください。
* **SyntaxError: Unexpected token ')'**：スクリプト末尾/ブロックの **かっこ対応** をご確認ください（`for { ... }` / `if { ... }` / `})();` など）。

---

## 🗺 ロードマップ（提案）

* [ ] パワーアップ（連射/スピード/シールド）
* [ ] コンボ倍率と一時表示UI
* [ ] ローカルランキング（`localStorage`）
* [ ] 敵バリエーション（Waveごとに形や色を変更）
* [ ] サウンドの軽量ミキサー（同時再生最適化）

---

## 🤝 コントリビュート

1. Issue で提案 or バグ報告
2. フォーク → ブランチ作成 → 変更
3. **PR**（スクショ・再現手順・期待挙動を明記）

コミットメッセージ例：

```
feat(game): add power-up items and combo multiplier
fix(audio): avoid overlapping beeps by reusing GainNode
docs(readme): add screenshots and deployment steps
```

---

## 🧾 ライセンス

* 例：**MIT License**（任意で変更可）。`LICENSE` ファイルを追加してください。

---

## 🙌 クレジット

* Design & Development: @your-handle
* Special thanks: playtesters & feedback contributors

---

### 英文サマリ（READMEの先頭に英語が必要な場合）

> **INVADERS NEO** is a single-file, Space-Invaders-like mini game built with HTML5 Canvas. Modern glass/neon UI, keyboard & touch controls, hi‑DPI ready. Clone, open `index.html`, and play. Deploy easily to GitHub Pages.
