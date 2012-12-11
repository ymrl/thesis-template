修士論文・卒業論文用LaTeXテンプレート
=====================================

慶應義塾大学湘南藤沢キャンパス(SFC)の修士論文用のテンプレートです。オリジナルは
[@kurokobo](http://twitter.com/kurokobo) による
[卒業論文用テンプレート](http://wiki.kurokobo.com/index.php?LaTeX) ですが、
以下のような改造を加えています。

* SFCの修士論文フォーマットに準拠。  
  [大学院ガイド](http://www.sfc.keio.ac.jp/students_mag/class/mag_guide/index.html) に基づいて、
  表題紙やアブストラクトを調整してあります。
* デザインの調整。  
  バインダー綴じのための余白設定を両面印刷に対応させました。
* BibTeXへの対応。  
  オリジナルのテンプレートでは BibTeX を使えないので、対応させました。
* UTF-8 化。  
  そろそろ内部的にも UTF-8 を使用する UpTeX が主流になってきているみたいなので、
  すべてのファイルが UTF-8 になっています。
  TeXShopなどのソフトウェアを使用する場合には設定の変更が（たぶん）必要です。
* Makefile の同梱。  
  Mac OS X や Linux のような Unix 系の OS であれば `make` 
  コマンドのみでコンパイルできるように Makefile を同梱しました。
* .gitignore の同梱。  
  git でファイル管理をしやすいように .gitignore を同梱しました。

サンプル
-------
2通りの生成例を用意しています。

* [sample_binder_twoside.pdf（バインダー用余白設定あり・両面印刷用）](http://ymrl.github.com/thesis-template/sample_binder_twoside.pdf)：配布している構成で`make`コマンドを実行した状態
* [sample_nobinder_oneside.pdf（バインダー用余白設定なし・片面印刷用）](http://ymrl.github.com/thesis-template/sample_nobinder_oneside.pdf)

使い方
-----
以下のコマンドを実行することで、 PDF を生成できます。

    % make

`make` コマンドが使用できない場合は、以下のようなコマンドを使用してください。

    % platex -kanji=utf8 main
    % pbibtex -kanji=utf8 main
    % platex -kanji=utf8 main
    % platex -kanji=utf8 main
    % dvipdfmx -p a4 main

なお、`\cite` コマンドを使用していない場合、 pbibtex コマンドでエラーが出ます。
この場合は、 `make` コマンドも使用できなくなるので、 Makefile を以下のように修正してください。

    all:
    	platex    -kanji=utf8 main
    	# pbibtex   -kanji=utf8 main 
    	# platex    -kanji=utf8 main 
      # この2行をコメントアウトする
    	platex    -kanji=utf8 main
    	dvipdfmx  -p a4 main

以下のコマンドで、生成されたすべてのファイルを削除します。

    % make clean

GitHubで論文を管理するには
----------------------
GitHub上にmy-thesisのようなリポジトリーを作って、以下のようにコマンドを実行してください。

    git clone git://github.com/ymrl/thesis-template.git my-thesis
    cd my-thesis
    git remote set-url remote git@github.com:myname/thesis.git
    git push origin master


その他
-----
上記の方法でコンパイルすると生成される PDF ファイルを参照してください。
また、 Blog にも随時情報を追加しておりますのでご覧ください。
http://mkdir.g.hatena.ne.jp/ymrl/

ライセンス
---------
オリジナルのテンプレートについては（おそらく） @kurokobo 
に著作権があります。
私が改造した部分についてはすべての権利を放棄いたします。
