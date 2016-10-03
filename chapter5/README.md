## oslo.messaging を使った通知処理の実装
　ここからは oslo.messaging が提供するもう一つの `通知 (Notification)` 機能について具体的な使い方について詳しく解説して行きます。  
　通知機能の用途についは OpenStack プロジェクトにおいてどのように使われているかの実例を紹介しますが、一般的にどういったユースケースで使われるかについて紹介します。  
　oslo.messaging の通知機能はもともと、サードパーティのシステムに対して非同期に通知を送る仕組みとして提供されており、RPC が特定のサービス (OpenStack の場合はコンポーネント) に閉じた仕組みであるのに対して、通知機能はシステムワイドに共通のイベントを発行し、システム全体における状態を把握するのに役立ちます。  
　例えば、以下のような EC サービスの例で RPC と通知機能のユースケースについて考えてみます。  

![Notification use-case](https://gist.github.com/userlocalhost2000/627c0f16516fb9a351b68a494751128c/raw/f5775695ca2ae6e6afb8c3ab1968ef3766c6f107/notification-usecase.png)

　ここでは各サービスが RPC API を提供し連携して、一つの EC サービスを提供していると仮定します。ここで、各サービスが利用履歴や検索キーワードなどの統計情報を集積したい場合に Notification 機能が役に立ちます。また各通知に対して、細かくフィルタ設定をおこなうことができるため、様々な粒度での通知処理をおこなう仕組みを提供できます。  
　それではサンプルを通じて、通知処理の実装方法について解説して行きます。  

---

* 5-1. [実装](https://github.com/userlocalhost2000/draft-oslo.messaging/tree/master/chapter5/chapter5-1)
* 5-2. [OpenStack (Ceilometer) の利用例](https://github.com/userlocalhost2000/draft-oslo.messaging/tree/master/chapter5/chapter5-2)