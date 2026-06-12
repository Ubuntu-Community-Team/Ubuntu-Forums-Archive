---
title: "I need some software that can recognize email adress out of a doc-file"
date: 2011-01-28
forum: General Help
---

### Post by score100 on 2011-01-28
so the thread title says it all I guess, for creating a  mailing list I need  a software that can do that. Other formats like txt or rtf would be great too, as I can easily convert.
best thanks in advance

(I've been googling a lot before i opened this thread, so no flaming :P )

---

### Post by flipper T on 2011-01-28
have you looked into mail merge in open office writer ? that will do the trick,

either dive straight into the wizard or f1 for help.

---

### Post by HermanAB on 2011-01-28
$ man fgrep

---

### Post by nothingspecial on 2011-01-28
```
\b[A-Z0-9._%+-]+@[A-Z0-9.-]+\.[A-Z]{2,4}\b
```

or maybe

```
^.+@[^\.].*\.[a-z]{2,}$
```

Depending wether email addresses are on single lines or anywhere. There are many many permutations.

have a look here

[http://regexlib.com/CheatSheet.aspx](http://regexlib.com/CheatSheet.aspx)

---

### Post by score100 on 2011-03-03
bit late, but thanx a lot guys!! :D

---

