---
title: "SCIM custom IME not working"
date: 2010-09-01
forum: General Help
---

### Post by Killeralgae on 2010-09-01
I have been using SCIM, trying to make an IME so I can type in Egyptian hieroglyphs ([http://en.wikipedia.org/wiki/Template:Unicode_chart_Egyptian_Hieroglyphs](http://en.wikipedia.org/wiki/Template:Unicode_chart_Egyptian_Hieroglyphs)). I have modified the Amharic keyboard to this end.

I first went in to the configuration file, and replaced Amharic characters with Egyptian ones. I'm sure I didn't touch anything else. When I used this IME file I either got the normal English keys, or nothing.

Then, I tried writing my own. I'm getting the same result.

I don't know what the problem could be. I did register the file in m17n.

This is the .mim I made. 

```
(input-method eg heiro)

(description Test
")

(title "Heiro")

(map
 (map

  ("q" &#78350;)
  ("w" &#78193;)
  ("e" &#78814;)
  ("r" &#77963;)
  ("t" &#78799;)
  ("t\" &#78680;)
  ("y" &#78284;)
  ("y\" &#78829;)
  ("u" &#77952;)
  ("i" &#78283;)
  ("o" &#77981;)
  ("p" &#78506;)
  ("a" &#78143;)
  ("s" &#78580;)
  ("s\" &#78467;)
  ("d" &#77991;)
  ("f" &#78225;))
  ("m" &#78163;)
  ))

(state
 (init
  (map)))

;; Local Variables:
;; coding: utf-8
;; mode: lisp
;; End:
```

Thank you, have some popcorn! :popcorn:

---

