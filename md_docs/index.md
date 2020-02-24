# ⭐️ Reactを使う準備
#### nodebrewのインストール
**・nodebrew とは**
node.jsのバージョンを管理するためのツール
一つの環境に複数バージョンのNode.jsを導入することが出来る
:hushed:node.jsって何？
　⇨サーバサイドで動くjavascript（javascriptは本来クライアントサイドで動く言語）
:neutral_face:なんで必要なの？
　⇨npmのバージョン互換性が問題になることが多いから
:confounded:npmって何？
　⇨Node Pacckage Managerの略で、パッケージ管理システムの一つ
　 パッケージとは、Node.jsのあらかじめ用意されている便利機能がまとまったもの

つまり、Node.jsの便利機能がまとまったパッケージというものを管理している**npm**のバージョンの互換性が問題になることが多いからnodebrewが必要ぽい・・・（不安）


**・nodebrewをインストールしてセットアップ**
※$は自分が作業したいフォルダを指定

```
$ brew install nodebrew
$ nodebrew setup
```

そうしたらこんな表示が・・・

```
========================================
Export a path to nodebrew:

export PATH=$HOME/.nodebrew/current/bin:$PATH
========================================
```

これで**パスが通せる**みたい
:hushed: パスを通すって何？
　⇨コマンドが格納されているパスを登録すること
　 例pwdとコマンドを打ったら`/bin/pwd`を実行した時と同じ動作をするようにする
　`$ export PATH=/xxx/bin`

この**nodebrew用のパス**を`.bash_profile`に追加する
:dizzy_face: .bash_profileってなんじゃい・・・
　⇨ログインシェルがbashの状態でログインしたときに読み込まれる設定ファイル
　　シェルにはいくつか種類があって

```
$ echo $SHELL
```
で確認できる！
私の場合は、

```
/bin/zsh
```
って出てきたから、`zsh`がログインシェルみたい
PATHの設定等だけであれば .bash_profile がそのまま使えるようなので、.bash_profileにnodebrew用のパスを追加する

```
$ cd
$ vim ~/.bash_profile
```

ってやると
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/481717/a9a2bb9a-7747-7112-d05f-79fe32c2ffa8.png)

って出てくる(これは追加後の画面)
初めは何も表示されていないので、この画面で`a`と入力する。(これでINSERTモードになる)
すると
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/481717/6de8ace9-ee1c-0dcb-cf9b-76d85426942b.png)
INSERTモードになるので、ここにさっきのPATHを追加！
そしたら、`esc`を入力（これでコマンドモードになる）
コマンドモードで`:wq`と入力すると「保存して終了」してくれるので、`:wq`を入力
(詳しくは「viコマンド」で検索〜〜〜)

これで.bash_profileにPATHを保存できたので、

```
$ source ~/.bash_profile
```
これで.bash_profileを読み込む（.bash_profileはログイン時しか読込されないので、ここで明示的に読み込んであげる）


####ようやくNode.jsのインストール

自分の作業したいディレクトリまで移動

```
$ nodebrew install-binary stable
```

これで安定版のNode.jsがインストールできる

```
$ nodebrew ls
```

これで自分がインストールしたNode.jsのバージョンが確認できる
私がインストールしたのは`v12.16.1`!

`create-react-app`コマンドが使えるように準備していく！
:rolling_eyes:　`create-react-app`って？
　⇨Facebookが提供しているCLI(Command Line Interface)ツールのこと
　　新規のReactプロジェクトを設定済みの開発者向けwebpackを使って始められる
つまり、`create-react-app`を使えばよくわかんない設定をすでに設定してくれている状態でReactを使うことができるみたい！

```
$ npm install create-react-app
```
これでインストールしようとしてみたけど、エラーが出てるっぽい・・・

```
npm WARN saveError ENOENT: no such file or directory, open '/Users/username/projects/todo_react/package.json'
npm WARN enoent ENOENT: no such file or directory, open '/Users/username/projects/todo_react/package.json'
npm WARN todo_react No description
npm WARN todo_react No repository field.
npm WARN todo_react No README data
npm WARN todo_react No license field.
```
なんかこんな感じ・・・
調べてみると

```
$ sudo npm install -g create-react-app
```
これならいけるっぽいのでこれを実行
:confused:　sudoって何なのさ
　⇨
