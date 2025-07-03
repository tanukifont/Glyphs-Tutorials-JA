原文: [Install Glyphs for all users](https://glyphsapp.com/learn/install-glyphs-for-all-users)
# すべてのユーザーにGlyphsをインストールする

チュートリアル

[ インストール ](https://glyphsapp.com/learn?q=installation)

執筆者: Rainer Erich Scheichelbauer

2021年3月7日更新（初版公開：2015年9月23日）

研究室など、一台のマシンで多くのユーザーにGlyphsやGlyphs Miniをインストールする必要がありますか？ここでは、それを素早く行う方法を紹介します。

## 最新の安定版をダウンロードする

常に[Glyphs 3の最新の安定版](https://updates.glyphsapp.com/latest3.php)を指すダウンロードリンクがあります。Appフォルダに直接`curl`できます。
```
curl https://updates.glyphsapp.com/latest3.php > ~/Desktop/Glyphs3.app.zip
unzip -o ~/Desktop/Glyphs3.app.zip -d /Applications
rm ~/Desktop/Glyphs3.app.zip
```
Glyphs 2についても同様です。もしそのバージョンをまだインストールする必要がある場合は、
```
curl https://updates.glyphsapp.com/latest2.php > ~/Desktop/Glyphs.app.zip
unzip -o ~/Desktop/Glyphs.app.zip -d /Applications
rm ~/Desktop/Glyphs.app.zip
```
そして、誰が推測したでしょうか、[Glyphs Miniの最新の安定版](https://updates.glyphsapp.com/latestMini2.php)を指すリンクもあります。さて、どうぞ。
```
curl https://updates.glyphsapp.com/latestMini2.php > ~/Desktop/Glyphs\ Mini.app.zip
unzip -o ~/Desktop/Glyphs\ Mini.app.zip -d /Applications
rm ~/Desktop/Glyphs\ Mini.app.zip
```

## すべてのユーザー向けにアプリをアンロックする

Macで`.glyphs3License`、`.glyphs2License`、または`.glyphsMini2License`ファイルを開くと、Glyphsは現在のユーザーで登録されます。しかし、*すべての*（将来の）ユーザーが登録されたGlyphsにアクセスできるべき場合はどうすればよいでしょうか？ここにトリックがあります。インストールプロセスを`sudo`で実行すると、登録はユーザーのライブラリではなく、Mac全体のライブラリに保存されます。そこで、ライセンスファイルをデスクトップに置き、ターミナルでこのコマンドを実行します。
```
sudo /Applications/Glyphs\ 3.app/Contents/MacOS/Glyphs\ 3 -disableUI 1 "~/Desktop/file.glyphs3License"
```

### プロのヒント
ターミナルコマンドに` -SUEnableAutomaticChecks 1 `という追加オプションを検討してください。これにより、自動アップデートチェックと新しいアプリバージョンのインストールが有効になります。非常にお勧めです。

あるいは、Glyphs 2の場合：
```
sudo /Applications/Glyphs.app/Contents/MacOS/Glyphs -disableUI 1 "~/Desktop/file.glyphs2License"
```
あるいは、Glyphs Miniの場合：
```
sudo /Applications/Glyphs\ Mini.app/Contents/MacOS/Glyphs\ Mini -disableUI 1 "~/Desktop/file.glyphsMini2License"
```
言うまでもなく、`file.glyphs3License`などを*あなたの*ライセンスファイルの名前（おそらくメールで受け取ったもの）に置き換えてください。これは、Glyphsのコピーを`/Applications`フォルダに入れ、ダウンロード後にアプリの名前を変更していないことを前提としています。そして、`disableUI 1`オプションがGlyphsをヘッドレスモードで、つまりユーザーインターフェースを起動させずに実行することは、おそらく推測できたでしょう。

### プロのヒント
それぞれの行を`-disableUI 1`まで（それを含めて）コピーし、ターミナルにペーストし、スペースを追加し、次にライセンスファイルをターミナルウィンドウにドラッグします（これにより、ライセンスファイルへのパスが便利に挿入されます）。そして、Returnキーを押します。

ああ、そしてもし学校の研究室で展開しているなら、マシンにライセンスファイルを残さないでください。親切にしてください。
```
rm ~/Desktop/*License
```
ありがとうございます。

### すべてのユーザー向けのスクリプトとプラグイン

実は、スクリプトやプラグインでも同じことができます。スクリプトフォルダとプラグインフォルダを、Glyphsのシステム全体のApplication Supportフォルダに移動させるだけです。ターミナルでこれらの行を実行して、Glyphs 3に必要なフォルダを作成します。

### 注意
スクリプトとプラグインはGlyphsのみに関連し、Glyphs Miniには関連しません。もしGlyphs Miniを展開しているなら、次の章に進むことができます。

```
sudo mkdir "/Library/Application Support/Glyphs 3/"
sudo mkdir "/Library/Application Support/Glyphs 3/Scripts/"
sudo mkdir "/Library/Application Support/Glyphs 3/Plugins/"
```
Glyphs 2の場合：
```
sudo mkdir "/Library/Application Support/Glyphs/"
sudo mkdir "/Library/Application Support/Glyphs/Scripts/"
sudo mkdir "/Library/Application Support/Glyphs/Plugins/"
```
さて、お気に入りのGitHubスクリプトリポジトリをクローンし、Mac上のすべてのユーザーが利用できるように簡単にできます。これらの行を（はい、すべて一度に！）ターミナルにコピー＆ペーストしてください。Glyphs 3用です。
```
sudo git clone https://github.com/mekkablue/Glyphs-Scripts.git "/Library/Application Support/Glyphs 3/Scripts/mekkablue/"
sudo git clone https://github.com/schriftgestalt/Glyphs-Scripts.git "/Library/Application Support/Glyphs 3/Scripts/schriftgestalt/"
sudo git clone https://github.com/hagenburger/glyphs-export-and-install.git "/Library/Application Support/Glyphs 3/Scripts/hagenburger/"
sudo git clone https://github.com/Tosche/Glyphs-Scripts.git "/Library/Application Support/Glyphs 3/Scripts/Tosche/"
sudo git clone https://github.com/Mark2Mark/Glyphsapp-Scripts-Free.git "/Library/Application Support/Glyphs 3/Scripts/Mark2Mark/"
sudo git clone https://github.com/huertatipografica/huertatipografica-scripts.git "/Library/Application Support/Glyphs 3/Scripts/huertatipografica/"
sudo git clone https://github.com/weiweihuanghuang/wei-glyphs-scripts.git "/Library/Application Support/Glyphs 3/Scripts/weiweihuanghuang/"
sudo git clone https://github.com/justanotherfoundry/freemix-glyphsapp.git "/Library/Application Support/Glyphs 3/Scripts/freemix/"
sudo git clone https://github.com/m4rc1e/mf-glyphs-scripts.git "/Library/Application Support/Glyphs 3/Scripts/MarcFoley/"
sudo git clone https://github.com/simoncozens/GlyphsScripts.git "/Library/Application Support/Glyphs 3/Scripts/SimonCozens/"
sudo git clone https://github.com/harbortype/glyphs-scripts.git "/Library/Application Support/Glyphs 3/Scripts/harbortype/"
```
またはGlyphs 2用：
```
sudo git clone https://github.com/mekkablue/Glyphs-Scripts.git "/Library/Application Support/Glyphs/Scripts/mekkablue/"
sudo git clone https://github.com/schriftgestalt/Glyphs-Scripts.git "/Library/Application Support/Glyphs/Scripts/schriftgestalt/"
sudo git clone https://github.com/hagenburger/glyphs-export-and-install.git "/Library/Application Support/Glyphs/Scripts/hagenburger/"
sudo git clone https://github.com/Tosche/Glyphs-Scripts.git "/Library/Application Support/Glyphs/Scripts/Tosche/"
sudo git clone https://github.com/Mark2Mark/Glyphsapp-Scripts-Free.git "/Library/Application Support/Glyphs/Scripts/Mark2Mark/"
sudo git clone https://github.com/huertatipografica/huertatipografica-scripts.git "/Library/Application Support/Glyphs/Scripts/huertatipografica/"
sudo git clone https://github.com/weiweihuanghuang/wei-glyphs-scripts.git "/Library/Application Support/Glyphs/Scripts/weiweihuanghuang/"
sudo git clone https://github.com/justanotherfoundry/freemix-glyphsapp.git "/Library/Application Support/Glyphs/Scripts/freemix/"
sudo git clone https://github.com/m4rc1e/mf-glyphs-scripts.git "/Library/Application Support/Glyphs/Scripts/MarcFoley/"
sudo git clone https://github.com/simoncozens/GlyphsScripts.git "/Library/Application Support/Glyphs/Scripts/SimonCozens/"
sudo git clone https://github.com/harbortype/glyphs-scripts.git "/Library/Application Support/Glyphs/Scripts/harbortype/"
```
これらのスクリプトをインストールするなら、*vanilla*というライブラリもインストールするのが良い考えです。これは、PythonスクリプトでCocoaのユーザーインターフェースクラスにアクセスするための人気のあるラッパーで、上記のスクリプトの一部はこれを利用しています。
```
sudo git clone https://github.com/typesupply/vanilla.git "/Library/Application Support/Glyphs 3/Modules/vanilla/"
cd "/Library/Application Support/Glyphs 3/Modules/vanilla/"
sudo python3 setup.py install
```
またはGlyphs 2用：
```
sudo git clone https://github.com/typesupply/vanilla.git "/Library/Application Support/Glyphs/Modules/vanilla/"
cd "/Library/Application Support/Glyphs/Modules/vanilla/"
sudo python2.7 setup.py install
```
そして、これらのスクリプトをインストールしたら、`git checkout`で更新できます。Glyphs 3の場合はこのようになります。
```
cd "/Library/Application Support/Glyphs 3/Scripts/mekkablue/"; sudo git checkout
cd "/Library/Application Support/Glyphs 3/Scripts/schriftgestalt/"; sudo git checkout
cd "/Library/Application Support/Glyphs 3/Scripts/hagenburger/"; sudo git checkout
cd "/Library/Application Support/Glyphs 3/Scripts/Tosche/"; sudo git checkout
cd "/Library/Application Support/Glyphs 3/Scripts/Mark2Mark/"; sudo git checkout
cd "/Library/Application Support/Glyphs 3/Scripts/huertatipografica/"; sudo git checkout
cd "/Library/Application Support/Glyphs 3/Scripts/weiweihuanghuang/"; sudo git checkout
cd "/Library/Application Support/Glyphs 3/Scripts/freemix/"; sudo git checkout
cd "/Library/Application Support/Glyphs 3/Scripts/MarcFoley/"; sudo git checkout
cd "/Library/Application Support/Glyphs 3/Scripts/SimonCozens/"; sudo git checkout
cd "/Library/Application Support/Glyphs 3/Scripts/harbortype/"; sudo git checkout
```
…またはGlyphs 2用：
```
cd "/Library/Application Support/Glyphs/Scripts/mekkablue/"; sudo git checkout
cd "/Library/Application Support/Glyphs/Scripts/schriftgestalt/"; sudo git checkout
cd "/Library/Application Support/Glyphs/Scripts/hagenburger/"; sudo git checkout
cd "/Library/Application Support/Glyphs/Scripts/Tosche/"; sudo git checkout
cd "/Library/Application Support/Glyphs/Scripts/Mark2Mark/"; sudo git checkout
cd "/Library/Application Support/Glyphs/Scripts/huertatipografica/"; sudo git checkout
cd "/Library/Application Support/Glyphs/Scripts/weiweihuanghuang/"; sudo git checkout
cd "/Library/Application Support/Glyphs/Scripts/freemix/"; sudo git checkout
cd "/Library/Application Support/Glyphs/Scripts/MarcFoley/"; sudo git checkout
cd "/Library/Application Support/Glyphs/Scripts/SimonCozens/"; sudo git checkout
cd "/Library/Application Support/Glyphs/Scripts/harbortype/"; sudo git checkout
```
これらの行をターミナルにペーストし、1、2分待てば、すべて完了です。

かなり壮大ですね。

## Adobe Fontsフォルダへの書き込みアクセス権

研究室のコンピュータにはAdobeアプリがありますか？ついでに、Adobe Fontsフォルダの読み書き権限を変更すべきです。この行をターミナルにコピー＆ペーストするだけです。
```
mkdir /Library/Application\ Support/Adobe/Fonts/
sudo chmod o+rw /Library/Application\ Support/Adobe/Fonts/
```
そうすれば、すべてのユーザーが[Adobeアプリでフォントをテスト](testing-your-fonts-in-adobe-apps.md)できるようになります。クールですね！

## ローカルユーザー（sudoなし）

もし*ローカル*ユーザーのみにインストールする場合は、Glyphs 3の*ウインドウ > プラグインマネージャ*を使用するのが最善です。そこには、考えられるすべてのモジュール、スクリプト、プラグインがあります。

### 続きを読む
プラグイン、スクリプト、モジュールのインストールについては、[Glyphsを拡張する](extending-glyphs.md)チュートリアルで詳しく説明しています。

もしGlyphs 2用にすべてのスクリプトを素早くインストールしたいなら、それはかなり面倒な作業になる可能性がありますが、上記と同じことを`sudo`なしで行い、スクリプトを*ユーザー*ライブラリにインストールできます。コピー＆ペーストが楽になるように、ターミナルコマンドのセットはこちらです。
```
git clone https://github.com/mekkablue/Glyphs-Scripts.git ~/Library/Application\ Support/Glyphs/Scripts/mekkablue/
git clone https://github.com/schriftgestalt/Glyphs-Scripts.git ~/Library/Application\ Support/Glyphs/Scripts/schriftgestalt/
git clone https://github.com/hagenburger/glyphs-export-and-install.git ~/Library/Application\ Support/Glyphs/Scripts/hagenburger/
git clone https://github.com/Tosche/Glyphs-Scripts.git ~/Library/Application\ Support/Glyphs/Scripts/Tosche/
git clone https://github.com/Mark2Mark/Glyphsapp-Scripts-Free.git ~/Library/Application\ Support/Glyphs/Scripts/Mark2Mark/
git clone https://github.com/huertatipografica/huertatipografica-scripts.git ~/Library/Application\ Support/Glyphs/Scripts/huertatipografica/
git clone https://github.com/weiweihuanghuang/wei-glyphs-scripts.git ~/Library/Application\ Support/Glyphs/Scripts/weiweihuanghuang/
git clone https://github.com/justanotherfoundry/freemix-glyphsapp.git ~/Library/Application\ Support/Glyphs/Scripts/freemix/
git clone https://github.com/m4rc1e/mf-glyphs-scripts.git ~/Library/Application\ Support/Glyphs/Scripts/MarcFoley/
git clone https://github.com/simoncozens/GlyphsScripts.git ~/Library/Application\ Support/Glyphs/Scripts/SimonCozens/
git clone https://github.com/harbortype/glyphs-scripts.git ~/Library/Application\ Support/Glyphs/Scripts/harbortype/
```
そして、まだGlyphs 2で、vanillaをローカルにインストールするには、「Glyphs > 環境設定 > アドオン > モジュール」に進み、「モジュールをインストール」ボタンをクリックするだけでも可能です。ボタンの隣に緑色のチェックマークが表示されたら、モジュールはインストールされ、すべてのスクリプトが「スクリプト」メニューで使用できるようになります。アプリを再起動するか、Optionキーを押しながら「スクリプト > スクリプトを再読み込み」（Cmd-Opt-Shift-Y）を選ぶ必要があるかもしれません。そうすれば、すべてのスクリプトがユーザーの「スクリプト」メニューに表示されるはずです。

その方法でスクリプトをインストールしたら、これらを使って最新バージョンに更新できます（はい、頻繁に変わります）。
```
cd ~/Library/Application\ Support/Glyphs/Scripts/mekkablue/; git checkout
cd ~/Library/Application\ Support/Glyphs/Scripts/schriftgestalt/; git checkout
cd ~/Library/Application\ Support/Glyphs/Scripts/hagenburger/; git checkout
cd ~/Library/Application\ Support/Glyphs/Scripts/Tosche/; git checkout
cd ~/Library/Application\ Support/Glyphs/Scripts/Mark2Mark/; git checkout
cd ~/Library/Application\ Support/Glyphs/Scripts/huertatipografica/; git checkout
cd ~/Library/Application\ Support/Glyphs/Scripts/weiweihuanghuang/; git checkout
cd ~/Library/Application\ Support/Glyphs/Scripts/freemix/; git checkout
cd ~/Library/Application\ Support/Glyphs/Scripts/MarcFoley/; git checkout
cd ~/Library/Application\ Support/Glyphs/Scripts/SimonCozens/; git checkout
cd ~/Library/Application\ Support/Glyphs/Scripts/harbortype/; git checkout
```
これらの行をターミナルにペーストし、1、2分待てば、準備完了です！そして繰り返しになりますが、これはGlyphs 2用です。Glyphs 3では、すべてのモジュール、スクリプト、プラグインは、「ウインドウ > プラグインマネージャ」経由でワンクリックでインストールできます。

---

更新履歴 2016-09-25: Mark2Markリポジトリのリンクを修正、JAF、SimonCozens、Marc Foleyのリポジトリを追加。

更新履歴 2017-10-28: vanillaのインストール手順を更新、いくつかの誤字を修正。ターミナルのフォーマットを更新。

更新履歴 2019-06-18: ローカルパスを/Desktopから~/Desktopに修正。Mark2Markのリンクを更新、hagenburgerとharbortypeのスクリプトを追加、ローカルインストールガイドを追加。

更新履歴 2019-09-01: スクリプトを最新バージョンに簡単に更新するためのgit checkoutコマンドを追加。

更新履歴 2019-09-10: gitのリンクに.gitサフィックスを追加。

更新履歴 2019-10-22: 誤字を修正。

更新履歴 2021-01-14: Glyphs 3向けに更新。

更新履歴 2021-01-20: SUEnableAutomaticChecksに関するヒントを追加。

更新履歴 2021-02-03: ターミナルコマンドのいくつかのタイプミスを修正。

更新履歴 2021-03-05: Glyphs 3用のターミナルコマンドを修正、大文字小文字の扱いを変更。