# RubyMotion Kaigi 2013 レポート

書いた人 : 海老沢 聡 ([@satococoa](https://twitter.com/satococoa))


## はじめに

この記事は [RubyKaigi 2013](http://rubykaigi.org/2013) 前日の 5/29(水) に開催された [RubyMotion Kaigi 2013](http://connpass.com/event/2095/) のレポート記事です。

RubyMotion Kaigi 2013 は参加者 100 名と小規模ながら、日本では初めて開催された RubyMotion のカンファレンスです。


## 開催概要

- 開催日: 2013 年 5 月 29 日 (水)
- 開催場所: 株式会社ミクシィ 様
- 主催: [RubyMotion JP](http://rubymotion.jp)
- 公式ページ: [RubyMotion Kaigi 2013](http://connpass.com/event/2095/)


## 開催までの流れ

現在、日本の RubyMotion コミュニティである [RubyMotion JP](http://rubymotion.jp) では月に 1 回 "RubyMotion もくもく会" と称し、RubyMotion に関することを自由に実践する勉強会を開催しています。

そのもくもく会の最中に、今年 (2013 年) の 3 月にベルギーのブリュッセルで開催された [#inspect 2013 - RubyMotion Conrefence](http://www.rubymotion.com/conference/) の話題になり、その際に「もし Laurent さんが RubyKaigi で日本にいらっしゃるのならそれに合わせて日本でもカンファレンスをやってみたらどうか？」という案が挙がりました。

カンファレンスとは言っても、前述のようにベルギーで世界規模のカンファレンスが開催された直後であるため、日本における RubyMotion の現状やもともと Objective-C で iOS アプリケーションを開発していた人の RubyMotion の印象を話してもらうなどの独自のコンテンツがある方が楽しいのではないか、などと議論し、今回のような形での開催となりました。

企画・準備・当日の運営までもくもく会の常連メンバーが中心となって進めてゆきましたが、せっかく日本で開催するのであれば東京だけではなく、以前から RubyMotion に関するイベントを複数回の開催されている福岡のコミュニティとも協力したいと思い、Ruby Business Commons 最首さんにも声をかけ、ご協力いただきました。


## 当日の様子

平日の夕方 18:30 という比較的早い時間からの開催であったためドタキャン等が心配されましたが、蓋を開けてみると開始時間直後でも 70% くらい、最終的には 80% 以上の参加者が参加されていた感触です。


### 基調講演: Laurent Sansonetti (@lrz) さん

なんと、冒頭は日本語でスピーチしてくれました。 (手元の iPhone に watson さん監修のローマ字メモがあったそうです。)

日本語で自己紹介と、スト 2 の地図を使用してベルギーの位置を確認した後は普通に英語で RubyMotion についての紹介をしていただきました。

RubyMotion のリリースから 1 年が経ったこと、数多くの RubyMotion 製の iOS アプリケーションが App Store で配布されてることなど。

その中でも RubyMotion 2.0 についての話が、現在 RubyMotion を使用している人にとっては特に興味深かったかと思われます。

質疑応答では以下の2つが出されました。

Q. CRuby 2.0 の機能 (Refinements, Keyword Arguments, ..etc.) は RubyMotion でもサポートする予定ですか？  
A. その予定はあるけれども、すぐに出来るとは限らない。特に Keyword Arguments は文法的に Objective-C のメソッドのシグネチャとバッティングしてしまうところがあり、扱いが難しい。

\# TODO: ust 見ながら内容についてもう少し詳しく述べる


### 日本における RubyMotion の現状: Ruby Business Commons 最首さん

RubyMotion のみに関わらず、mruby, mobiruby, Unity など、組み込みやスマートフォンという大きな括りで昨今 Ruby が注目を浴びているというお話をしていただきました。

やはり東京と比較しても福岡では特に組み込みの盛り上がりが大きいらしいという印象を持ちました。


### RubyMotion 2.0: @watson1978 さん

<script async class="speakerdeck-embed" data-id="9f6aa220aaaa01303c9b3e7747c857c8" data-ratio="1.2994923857868" src="//speakerdeck.com/assets/embed.js"></script>

@watson1978 さんは MacRuby の主要なコミッターであり、かつ HipByte 社のメンバーとして日本からリモートで RubyMotion の開発に携わっていらっしゃいます。

まずは MacRuby との出会いやそのコミッターになる __契約__ を交わしたエピソードが公開されました。

その後は RubyMotion の仕組みや特徴についてのお話、RubyMotion 2.0 で搭載された以下の新機能の詳しい紹介をしていただきました。

**OS X Support**  
Mac OS X 用のアプリケーションが作れるようになりました。以下の点で MacRuby と比べて以下のような特徴があります。

- 事前にネイティブにフルコンパイルしているからパフォーマンスが良い
- スタティックライブラリーが使える
- require, eval, 標準ライブラリーが使えない

**Project Template**  
ユーザーが独自のテンプレートを作れる機能です。よく使う gem をあらかじめ Gemfile に書いておいたり、app_delegate.rb で @window をインスタンス化する以下のようなお決まりのコードをテンプレート化しておけます。

**Command-Line Plugin**  
ユーザー独自のサブコマンドを `motion` コマンドに追加できる機能です。@watson1978 さんがサンプルで作った [motion-doc](https://github.com/Watson1978/motion-doc) コマンドの紹介がありました。

**Common Build Directory**  
一度コンパイルした gem を他のアプリでも使い回せるようにし、ビルド時間を短縮する機能です。特に [BubbleWrap](http://bubblewrap.io) や [sugarcube](https://github.com/rubymotion/sugarcube) のような大きなライブラリを使うときに効果が発揮されるそうです。

**Weak Reference**  
弱参照をサポートする機能です。RubyMotion には ARC 同様のリファレンスカウンタによる GC が実装されています。オブジェクトを代入する際には自動的にリファレンスカウンタが上がるようになっているのですが、この `WeakRef` を使用することで、リファレンスカウンタを上げずにオブジェクトを参照することが出来ます。


質疑応答の際には Laurent さんから発表資料のデータに関する質問が飛んでいました。


### 実践 RubyMotion: @naoya_ito さん

<script async class="speakerdeck-embed" data-id="1cd72a90aaf701306ef82e07ed1e0849" data-ratio="1.33333333333333" src="//speakerdeck.com/assets/embed.js"></script>

アプリケーション実装者の視点から見た RubyMotion について発表していただきました。

まずは RubyMotion の特徴と簡単なコード例を示し、Objective-C の知識が無くても RubyMotion でアプリケーションを開発することは可能だが iOS の知識は必要である、という点について説明をしていただきました。

つまり Objective-C の代わりに言語を Ruby を使用しているだけであって、フレームワークは Cocoa Touch を使用しているのでフレームワークについての知識は必要になる (学ぶ必要がある) とのことです。

続いて、RubyMotion における `Object` クラスは `NSObject` クラスを継承している作りとなっているため、Cocoa (Touch) の API がそのまま呼べることについての説明がありました。

GCD を使うことによって並行処理も以下のコード例のように Ruby らしくスマートに書けます。

```
Dispatche::Queue.concurrent.async do
  image = UIImage.alloc.initWithData(
    NSData.dataWithContentsOfURL(url.nsurl)
  )

  Dispatch::Queue.main.sync do
    @imageView.image = image
  end
end
```

RubyMotion のメモリ管理についての説明もありました。

RubyMotion についての説明はここまでで、あとは (主にスベッた) ネタを交えながら実際に RubyMotion で開発する上での Tips や、定番のライブラリの紹介等がありました。

詳しくは [スライド](https://speakerdeck.com/naoya/shi-jian-rubymotion) を見ていただくと詳しく書かれていますので良いかと思われます。


### That Objective-C guy think about RubyMotion: @mfks17 さん

<script async class="speakerdeck-embed" data-id="36a786d0aab101303c9b3e7747c857c8" data-ratio="1.2994923857868" src="//speakerdeck.com/assets/embed.js"></script>

@mfks17 さんは RubyMotion 以前から iOS アプリケーションの開発を Objective-C でやっていらっしゃる方です。今回は元々 Objective-C の経験のある方から見た RubyMotion という観点から RubyMotion についてお話ししていただきました。

RubyMotion でアプリケーションの開発を行うにあたって、Xcode を使わずに済むという点を挙げられていました。特に設定に関してはわかりにくい GUI での設定ではなく、Rakefile にコードを書くという方法で完結できるのが良いとのことです。

デバッグに関しては RubyMotion では gdb を使ってコマンドラインでのデバッグが可能ですが、RubyMotion にも対応した IDE の [RubyMine](http://www.jetbrains.com/ruby/) を利用することにより、GUI でブレークポイントを置いたり、変数の中身を見たりできると紹介がありました。

RubyMine に関連して、RubyMotion で開発を行うにあたっての以下のような周辺ツールの紹介もありました。

- [motion-mode.el](https://github.com/ainame/motion-mode)
- [SublimeObjC2RubyMotion](https://github.com/kyamaguchi/SublimeObjC2RubyMotion)
- [SublimeRubyMotionBuilder](https://github.com/haraken3/SublimeRubyMotionBuilder)

最後にテストツールやフレームワークについての紹介がありました。
Objective-C で開発する際は OCUnit(SenTestingKit), Kiwi, GHUnit などが広く使われていますが、RubyMotion では MacBacon, motion-calabash などが使えるとのことです。
そして、テストを日々のワークフローの中に組み込んで習慣化することが大切であるという心がけのお話もありました。

@mfks17 さんは今後 RubyMotion に関わらず iOS の開発に関する勉強会の立ち上げを考えているとのことです。


### LT1 / #inspect 2013 - RubyMotion Conrefence の感想: 井上さん
[#inspect 2013 - RubyMotion Conrefence](http://www.rubymotion.com/conference/) に参加した日本人全 4 名のうちの一人、井上さんによる発表でした。カンファレンスに参加する経緯として井上さんのボスの考え方やカンファレンスでの印象に残った発表などについてお話しいただきました。


### LT2 / Dive into Joybox: @yonekawa さん

<script async class="speakerdeck-embed" data-id="1a93d7a0aa89013080c73e09fd6c9c49" data-ratio="1.33333333333333" src="//speakerdeck.com/assets/embed.js"></script>

RubyMotion でゲーム開発をするというテーマで発表していただきました。

[Joybox](https://github.com/rubymotion/Joybox) という [Cocos2D](http://www.cocos2d-iphone.org) と [Box2D](http://box2d.org) のラッパーの紹介と、それを使って作った実際に動作するデモがありました。

[Joybox](https://github.com/rubymotion/Joybox) は [#inspect 2013 - RubyMotion Conrefence](http://www.rubymotion.com/conference/) で発表されたライブラリで、@yonekawa さんは Joybox の最初のコントリビュータとして精力的に開発に関わっていらっしゃいます。

まだまだ仕事で使用するには機能が不足していて辛いとのことですが、今後の開発に期待したいところですね。


### LT3 / RubyMotionについて本気出して考えてみました: @ainame さん

<script async class="speakerdeck-embed" data-id="96dc0ab0ab0c0130efd85a101b549cb4" data-ratio="1.33333333333333" src="//speakerdeck.com/assets/embed.js"></script>

Emacs 用の RubyMotion の拡張である [motion-mode.el](https://github.com/ainame/motion-mode) を開発された「[神](http://d.hatena.ne.jp/naoya/20130322/1363921458)」こと @ainame さんの発表です。

実際に本気で仕事で RubyMotion を使うためにはどうしたらいいのか、というテーマでの発表でした。

業務で RubyMotion を使おうとした際のハードルとして、以下の 3 点が挙げられていました。

1. 覚えることが多い
1. 初心者が入門しづらい
1. 本当に業務で使えるか不安

しかし、以下の点によりむしろ Web アプリケーションの経験がある人にとっては、むしろ新規に Objective-C で iOS の開発を覚えるよりはむしろ始めやすいのではというお話でした。

- 開発スタイルが Web に近い: 使い慣れたエディタ、RSpec like なテスト、コマンドライン中心の開発スタイル、サーバー / クライアント双方を Ruby で書ける
- サポートの返答が速い: iOS の新しいバージョンへの対応も問い合わせへの対応も速い
- Ruby の力を信じる: rake, gem などの便利なツール、メタプログラミング、書いていて楽しい

@ainame さんは最近 [RubyMotionTokyo](http://rubymotion-tokyo.doorkeeper.jp) というコミュニティを立ち上げられました。現在、都内で隔週で meetup を開催されているので RubyMotion に関心のある方はぜひ参加されてはいかがでしょうか。


### LT4 / RubyMotion meets IRC: @ninjinkun さん

<script async class="speakerdeck-embed" data-id="d70369f0aafa0130da893e97780925f0" data-ratio="1.2994923857868" src="//speakerdeck.com/assets/embed.js"></script>

@ninjinkun さんは最近 [NJKWebViewProgress](https://github.com/ninjinkun/NJKWebViewProgress) というライブラリを作られて、世界でも注目されている開発者です。

最近 RubyMotion で社内システムのアプリを作っているらしいです。

今回は RubyMotion で IRC のクライアントアプリをつくってみたというお話ですが、RubyMotion では Ruby の文法でメタプログラミングができ、正規表現が使えるという特徴からテキストベースのプロトコルを扱うのに向いているのではないかということがモチベーションになっているそうです。

プロトコルパーサーを実装する際には node.js で書かれたコードを Ruby のコードに翻訳したらそのまま動作したり、CRuby で実装されたコードをコピー & ペーストしたらそのまま動いたりしたそうです。

ソケットの実装には [motion-cocoapods](https://github.com/HipByte/motion-cocoapods) 経由で [GCDAsyncSocket](https://github.com/robbiehanson/CocoaAsyncSocket) を使うことで比較的用意に実装できたそうです。

View は小さな HTML テンプレートエンジンを実装し、UIWebView 上にクライアントサイドの HTML テンプレートを描画することで実装しているそうで、これも実際に動作しているところをデモしていただきました。


### Laurent さんへの Q&A コーナー

\# TODO: 動画を見ながら書く

Q. 現在 C++ で実装されたライブラリを使うには Objective-C でラップする必要がありますが、今後は直接 RubyMotion から使えるようになる予定はありますか？
A. 

Q. 割引は予定されていますか？  
A. RubyKaigi 割引で RubyKaigi 期間中は 15% 引きにするよ


## 参加レポートなどのまとめ

- [ツイートまとめ (Togetter)](http://togetter.com/li/510492)
- [Ustream](http://www.ustream.tv/channel/rubymotion-kaigi-2013)
- ブログ記事等 (順不同)
  - http://blog.ainam.me/2013/05/30/rubymotion-kaigi-misawa-suberu/
  - http://mog2dev.hatenablog.com/entry/2013/05/31/014938
  - http://d.hatena.ne.jp/mfks17/20130530/1369878790
  - https://www.evernote.com/shard/s9/sh/ba409673-122d-43a1-86b0-  ec12063cc991/22a85b8a08b65884c00846b38919038c
  - http://rochefort.hatenablog.com/entry/2013/05/30/004541
  - http://watson1978.github.io/blog/2013/06/03/rubymotion-kaigi-2013/


## その後の RubyMotion コミュニティの盛り上がり

継続的に開催されている RubyMotion 関連のコミュニティ / 勉強会は従来は [RubyMotion もくもく会](http://connpass.com/series/130/) しかありませんでしたが、この RubyMotion Kaigi 2013 の後に 2 つのコミュニティが立ち上がりました。

[RubyMotion もくもく会 in Osaka](http://connpass.com/event/2731/) (リンク先は第2回) は大阪で開催されているもくもく会です。

[RubyMotionTokyo](http://rubymotion-tokyo.doorkeeper.jp) は都内で隔週で meetup を実施しているコミュニティです。

また、業務で RubyMotion を使っている人も徐々に増えて来ているらしく、会場の参加者のみなさんに「RubyMotion で仕事をしている人はいますか？」と問い合わせたところ、5〜6人の方が手を挙げていらっしゃいました。

2012 年の 7 月に開催した [第一回 RubyMotion 勉強会](http://connpass.com/event/665/) のときは一人しかいなかったので、徐々に広がりつつある感触があります。


## まとめ



## 著者について
海老沢 聡 ([@satococoa](https://twitter.com/satococoa))

[株式会社イグニス](http://1923.co.jp) 所属。

[P4D デザイナー向けプログラム部](http://prog4designer.github.io) や [RubyMotion JP](http://rubymotion.jp) をやっています。
