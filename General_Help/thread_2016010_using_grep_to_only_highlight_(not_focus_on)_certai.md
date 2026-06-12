---
title: "using grep to only highlight (not focus on) certain words"
date: 2012-07-04
forum: General Help
---

### Post by Ohzed on 2012-07-04
whenever searching a "man" page for a particular program ( e.g man <program> | grep <word to highlight> ), how do I get it to just highlight the word specified using "grep" and also show the whole man page along with that? cause on the output it seems to just focus on some of the descriptions around the word I highlighted, and not show the whole man page with the grepped word highlighted in there.

---

### Post by msammels on 2012-07-04
I'm confused - you could simply:

```
man vi
```

To get the man page for vi... or you could also use:

```
apropos vi
```

Which is an alternative. Can you explain in detail what you mean exactly? If you're grepping for a search phrase, like a function or something, then I have no idea how to highlight :(

---

### Post by vasa1 on 2012-07-04
> **Ohzed said:**
> whenever searching a "man" page for a particular program ( e.g man <program> | grep <word to highlight> ), how do I get it to just highlight the word specified using "grep" and also show the whole man page along with that? cause on the output it seems to just focus on some of the descriptions around the word I highlighted, and not show the whole man page with the grepped word highlighted in there.
I don't think what you want is possible.

---

### Post by Vaphell on 2012-07-04
grep supports -A -B options allowing to print a defined number of lines before/after match, which allows to see bigger chunk of text. eg *grep -A 20 -B 20* will show match with 20 preceding and 20 following lines.

also you can try to hack it with sed and using color codes around the desired phrase
eg
```
$ echo $'abc def ghi\n111 def x\nxxx def a def' | sed 's/def/[COLOR="Blue"]^[[/COLOR][31m&[COLOR="Blue"]^[[/COLOR][m/g'
abc [COLOR="Red"]def[/COLOR] ghi
111 [COLOR="Red"]def[/COLOR] x
xxx [COLOR="Red"]def[/COLOR] a [COLOR="Red"]def[/COLOR]
```

**^[** is produced by CTRL+V,ESC

---

