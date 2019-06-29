# Unique URL

@suginoy

とちぎRuby会議08

---
## クローラー

---
## クローラー書いてて困ったこと

---
## 同じコンテンツを重複でクロールしたくない

---
## 同じとは

### この URL とこの URL は同じページだと思うんだけど...？

---
## URL の文字列が同じ？

- Ruby で `URI.parse` が返すオブジェクトの比較ではない。
- コンテンツが大事

---
## Q.1

- `http://example.com`
- `https://example.com`

---
## A.1

## 場合による

- http から https へリダイレクトしたりする。
- 同じこともある。

---
## Q.2
- `https://example.com`
- `https://example.com/`

---
## A.2

## たぶん同じ

- ブラウザのアドレスバーをコピると '/' が追加される？

---
## Q.3
- `https://example.com/path`
- `https://example.com/path/index.html`

---
## A.3

## 同じ

- Web の仕様( W3C か IETF あたりにあるはず)

---
## Q.4

- `https://example.com/aaa`
- `https://example.com/aaa/`

---
## A.4

## Web サーバーの設定による。

- "trailing slash + (webサーバー名)" でググれ

---
## Q.5

- `https://example.com/`
- `https://example.com/#`

---
## A.5

## 同じ

- `#` は Web サーバーには送られない

---
## Q.6

- `https://youtube.com`
- `https://m.youtube.com`

---
## A.6

## 場合による

- 自分がほしいものによる
- `<head>` に `< link rel="canonical">` があることが多い。

---
## Q.7

- `https://example.com/?A=1&B=2`
- `https://example.com/?B=2&A=1`

---
## A.7

## たぶん同じ

- 同じものが取れるなら

---
## Q.8

- `"https://example.com/aaa?_=123424324132143"`
- `"https://example.com/aaa?_=123424324013551"`

#### アクセス解析などで謎のパラメータが付いていることがある。

---
## A.8

## たぶん同じ

- 解析の結果、JavaScript の `Date.now()` を付けているらしい。
- Ruby と JavsScript で UNIX タイムスタンプが 3 桁違って地味に困っている人がたまにいる。

- Ruby
```
Time.now.to_i #=>  1561788592
```
- JavaScript
```
Date.now()    //=> 1561788661402
```

---
## Q.9

- 昨日の検索結果1ページ目
- 今日の検索結果1ページ目

---
## A.9

わからん

---
## 結論

# 同じかどうかは俺が決める
