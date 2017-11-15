# HoneyWaffleSDT5

（作業中）

## 振り飛車党評価関数（やねうら王のKPPT形式）
https://drive.google.com/open?id=1mvMtLTy5TM4GFBda-ppX-wEYKylVs7yx

予選リーグ、決勝トーナメントを通して使用した評価関数です。  
定跡で76歩や34歩を突かせると、だいたい飛車を振ります。  
定跡なしの場合、飛車先を突いて居飛車を指してしまうこともよくあります。

## 振り飛車「狂」評価関数（やねうら王のKPPT形式）
https://drive.google.com/open?id=11SSW-2b8VP0YEzEuN1PLwQSNS5FDr7NT

振り飛車党評価関数を作るための原液のような評価関数です。  
ただ飛車を振るだけの評価関数で、とても弱いです。  
やねうら王を魔改造し、居飛車を減点することで強引に振り飛車を高く評価させ、そこから教師局面を生成させて学習しました。  


振り飛車党評価関数は、以下の評価関数を試行錯誤しながらブレンドしたものです。

* 振り飛車「狂」評価関数

* ライブラリ申請した、elmo評価関数

* ライブラリ申請した、やねうら王rezero8評価関数

* やねうら王エンジン+elmo評価関数+振り飛車定跡で教師局面生成し、ゼロベースから学習した評価関数

戦型を気にしなければelmo(WCSC27)に6割以上は勝っていたと思いますが、居飛車で勝たないよう定跡で封印したので、振り飛車のみでは互角くらいかと思います。


## 定跡ファイル（やねうら王形式）

https://github.com/32hiko/HoneyWaffleSDT5/blob/master/waffle_book.db

WCSC27版の定跡をベースにしたものを初期状態としました。  
elmo(WCSC27)との対戦を繰り返し、振り飛車でいい感じの序盤になったら、振り飛車側の手だけ50手まで追加しています。  
また、評価値が急に下がるような局面では局面検討の結果で矯正しています。  
評価値的に多少不利（先手-100まで、後手は-200弱まで）でも、相手から特にいい手がなく差が広がらないものは採用しています。  
開発当初は評価関数も振り飛車党になりきっていないため、定跡を更新しつつ、評価関数も学習しつつのサイクルに乗せるまでは苦労しました。  
級位者がすべて目を通して手作業で追加しているので、不自然なものが結構あるかもしれません。  
評価関数側の成果により、初手58飛や後手での52飛は不要になりました。
