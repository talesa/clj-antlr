# Clj-Antlr with ANTLR alternative labels support

Fork of [`clj-antlr`](https://github.com/aphyr/clj-antlr/) supporting [ANTLRv4 alternative labels](https://github.com/antlr/antlr4/blob/master/doc/parser-rules.md#alternative-labels).
At the moment it's just a rather bad patch to the library for my personal purposes, I may try to 'refactor' it and make a pull request later.

Version left as `0.2.5-SNAPSHOT`

# How to use
Original way is broken, you can now use it as following
```
(require [clj-antlr.coerce :as coerce]
         [clj-antlr.interpreted :as interpreted])
(defn parse
  [grammar-file input-file]
  (let [input-string (slurp input-file)
        grammar-str (slurp grammar-file)
        grammar (interpreted/grammar grammar-str)
        m (interpreted/parse grammar {} input-string)
        e (coerce/tree->sexpr m)]
    e))
(parse "grammars/Json.g4" "data/test.json")
```
