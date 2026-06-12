---
title: "Command line syntax ('-' Vs. '--')"
date: 2009-12-30
forum: General Help
---

### Post by mahela007 on 2009-12-30
Some options are passed to shell commands preceded by a single dash '-'. Other preceded by two dashes '--'. (the manual or info pages for any command shows this). What's the difference between the two?

---

### Post by jollysnowman on 2009-12-30
"-" is used for a single letter option, while "--" is for words... For example, ```
javac -v
javac --verbose.
```

One can also specify options with "--", like ```
weather -f -i --city=AUSTIN --st=TX
``` (I think those are the right options, but it's something like that)

---

