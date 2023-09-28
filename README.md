
![](https://raw.githubusercontent.com/yKesamaru/modify_text_kousei_kun/master/img/eye_catch.png)

- [これはなにか](#これはなにか)
  - [注意](#注意)
- [想定するシーン](#想定するシーン)
- [詳細](#詳細)
  - [目標](#目標)
  - [環境](#環境)
  - [事前準備](#事前準備)
  - [日本語校正辞書の場所](#日本語校正辞書の場所)
  - [変更](#変更)
- [結果](#結果)


## これはなにか
- `VSCode機能拡張版テキスト校正くん`の日本語校正辞書に手を加えて自分色にする手順です。
- 設定でチェックを外してしまうとその他の用語が校正されなくなってしまう問題を解決したい場合に使用します。
  - （例）`VS Code`は`VSCode`にしたい。しかしながら`Japanese-proofreading › Textlint: 技術用語`（またはsettings.jsonの該当部分）のチェックを外してしまうと`Github`に波線がつかなくなってしまう。（`GitHub`）

  ![](https://storage.googleapis.com/zenn-user-upload/0d2065cbdae2-20220503.png)

### 注意
- 日本語校正辞書に手を加えること自体がテキスト校正くんを使用する根本的な意味を消失させる可能性を持ちます
- 辞書内容に間違いがある場合は慎重に確認の上、プルリクエストしましょう
  - 参考：[「Chatwork」は「Chatwork」であって「ChatWork」ではない ](https://note.com/dafujii/n/n1327a0490799)

## 想定するシーン
- プロジェクト内で統一された書式とテキスト校正くんの日本語校正辞書の一部に差異がある場合
- 個人で使用する場合において一部の表記にこだわりがある場合
- `C Spell`など他の拡張を使わない場合

## 詳細
### 目標
`VS Code`を`VSCode`に変更します。
### 環境
```log
$ uname -a
Linux host 5.13.0-40-generic #45~20.04.1-Ubuntu SMP Mon Apr 4 09:38:31 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux
$ code -v
1.66.2
x64
```
>  テキスト校正くん
リリース日
2018/6/26 19:51:42
最終更新
2022/3/4 19:09:52
識別子
ics.japanese-proofreading

### 事前準備
辞書のどの場所を変更したのか後から追えるようにgit管理します

![](https://storage.googleapis.com/zenn-user-upload/becada58ec15-20220503.png)
### 日本語校正辞書の場所
- `~/.vscode/extensions/ics.japanese-proofreading-1.1.0/node_modules/textlint-rule-preset-icsmedia/dict`
- `grep`を使って`VS Code`がどのファイルに登録されているのか調べたら、エディタで該当部分を変更します。
  ```log
  $ grep -ie vscode *
  prh_web_technology.yml:    pattern: VSCode
  ```
### 変更
`prh_web_technology.yml`ファイルについて以下のように変更しました。
![](https://storage.googleapis.com/zenn-user-upload/d7fd82fb0628-20220503.png)
変更したらVSCodeを再起動して完了です。

## 結果
![](https://storage.googleapis.com/zenn-user-upload/12282ba33dd4-20220503.png)
期待通りになりました。