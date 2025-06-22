---
title: ObsidianとGitHubの連携ガイド：初心者向け
source: https://claude.ai/public/artifacts/3cc31fc7-41a9-487e-940b-a7ffd0e2efd8
author:
  - "[[Claude]]"
published: 
created: 2025-06-22
description: ObsidianとGitHubの連携ガイド：初心者向け - Markdown document created with Claude.
tags:
  - clippings
  - obsidian
  - git
  - github_integration
  - version_control
  - backup
  - cloud_sync
  - multi_device_sync
  - file_recovery
  - repository
  - commit
  - push
  - pull
  - personal_access_token
  - obsidian_git
  - auto_backup
  - auto_push
  - authentication
  - setup_guide
  - beginner_guide
  - troubleshooting
  - git_installation
  - repository_creation
  - remote_connection
  - local_repository
  - change_history
  - file_versioning
  - collaboration
  - data_persistence
  - workflow_integration
---
## はじめに

このガイドでは、Obsidian（ノートアプリ）とGitHub（ファイル保存・共有サービス）を連携させる方法を説明します。この連携により、以下のメリットがあります：

- ノートの変更履歴を記録できる
- クラウドにバックアップできる
- 複数のデバイス間で同期できる
- 誤って削除した場合に復元できる

## 用語解説

まず、よく使う用語を簡単に説明します：

- **Git**: 変更履歴を記録するためのシステム（カメラのようなもの）
- **リポジトリ**: 変更履歴とファイルを保存する場所（アルバムのようなもの）
- **GitHub**: Gitリポジトリをインターネット上に保存するサービス（クラウドアルバムのようなもの）
- **コミット**: 変更を記録すること（写真を撮ること）
- **プッシュ**: ローカルの変更をGitHubに送ること（アルバムをクラウドにアップロードすること）
- **プル**: GitHubの変更をローカルに取得すること（クラウドからアルバムをダウンロードすること）

## 全体の流れ

今回行った手順の全体像は以下の通りです：

1. GitHubアカウントを作成
2. GitHubでリポジトリ（保存場所）を作成
3. パソコンにGitをインストール
4. Obsidian Vaultフォルダをリポジトリとして設定
5. ObsidianとGitHubを接続
6. Obsidian Gitプラグインをインストール

## 詳細な手順

### 1\. GitHubアカウントの作成

1. [GitHub](https://github.com/) にアクセス
2. Sign Up（登録）からアカウントを作成

### 2\. GitHubでリポジトリを作成

1. GitHubにログイン
2. 右上の「+」ボタン → 「New repository」をクリック
3. リポジトリ名を入力（例：「obisidiancursor」）
4. 「Create repository」ボタンをクリック

### 3\. Gitのインストール（すでに完了済み）

Macの場合：

```
brew install git
```

Windowsの場合：

- [Git for Windows](https://gitforwindows.org/) からダウンロード・インストール

### 4\. Obsidian Vaultをリポジトリとして設定

ターミナル（コマンドプロンプト）で以下の操作を行います：

```
# Obsidian Vaultフォルダに移動
cd /Users/satoutakehiko/Desktop/Vault

# Gitリポジトリとして初期化
git init

# 全ファイルをステージングに追加
git add .

# 初期コミット（変更を記録）
git commit -m "Initial commit"
```

### 5\. ObsidianとGitHubを接続

```
# リモートリポジトリを設定（GitHubと接続）
git remote add origin https://github.com/takeaiai/obisidiancursor.git

# 接続設定を確認
git remote -v

# GitHubにプッシュ（送信）
git push -u origin main
```

プッシュ時に認証が必要な場合：

- ユーザー名：GitHubのユーザー名
- パスワード：個人アクセストークン（通常のパスワードではなく）

### 6\. 個人アクセストークンの作成方法

1. GitHubにログイン
2. 右上のプロフィール画像 → Settings
3. 左メニュー最下部の「Developer settings」
4. 「Personal access tokens」→「Tokens (classic)」
5. 「Generate new token」→「Generate new token (classic)」
6. トークンの名前を入力（例：「Obsidian Git」）
7. 有効期限を選択
8. 「repo」にチェック
9. 「Generate token」ボタンをクリック
10. 表示されたトークンを保存（この画面を離れると二度と表示されません）

### 7\. Obsidian Gitプラグインのインストール

1. Obsidianアプリを開く
2. 設定（歯車アイコン）をクリック
3. 「コミュニティプラグイン」→「Browse」
4. 「Git」で検索
5. 「Obsidian Git」をインストールして有効化

## 日常的な使い方

### Obsidian Gitプラグインでの操作

Obsidianの左側のサイドバーにGitアイコンが表示されます。ここから：

1. **変更の確認**: 変更されたファイルが表示されます
2. **コミット**: 「Commit」ボタンで変更を記録
3. **プッシュ**: 「Push」ボタンでGitHubに送信
4. **プル**: 「Pull」ボタンでGitHubから取得

### 自動バックアップの設定（オプション）

Obsidian Gitプラグインの設定で：

1. 「Auto backup」を有効化
2. バックアップの間隔を設定（例：10分）
3. 「Auto push」を有効化すると自動的にGitHubに送信

## トラブルシューティング

### リポジトリが見つからないエラー

```
fatal: repository 'https://github.com/ユーザー名/リポジトリ名.git/' not found
```

原因と解決策：

- リポジトリ名のスペルミス → 正確な名前を確認して設定
- リポジトリが存在しない → GitHubで作成
- アクセス権限の問題 → 個人アクセストークンを確認

### 認証失敗エラー

```
fatal: Authentication failed for 'https://github.com/ユーザー名/リポジトリ名.git/'
```

原因と解決策：

- パスワードではなく個人アクセストークンを使用する
- トークンの権限不足 → 「repo」権限を持つ新しいトークンを作成

## まとめ

これで、ObsidianとGitHubの連携が完了しました。この設定により：

- Obsidianのノートが自動的にバックアップされます
- 変更履歴が記録されるので、以前のバージョンに戻すことができます
- 複数のデバイスで同じノートを編集・同期できます

この仕組みは最初は少し複雑に感じるかもしれませんが、一度設定してしまえば、あとは日常的な操作はとても簡単です。Obsidian Gitプラグインを使えば、ボタン一つでバックアップや同期が行えます。

Made with