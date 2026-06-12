---
title: "Gmail crashes firefox"
date: 2006-02-28
forum: General Help
---

### Post by ohzopants on 2006-02-28
Since yesterday, whenever I log into my gmail account I get the little red loading box in the top right and then firefox (1.5) just disappears.  No errors no nothing.  I have tried with and without other tabs open, I have not installed any new extensions recently, I don't know what's happening.  My gmail notifier is still reporting new messages, but I have to go to my other computer to actually see them.

Please help me

---

### Post by o_fortuna on 2006-02-28
[QUOTE=ohzopants]Since yesterday, whenever I log into my gmail account I get the little red loading box in the top right and then firefox (1.5) just disappears.  No errors no nothing.  I have tried with and without other tabs open, I have not installed any new extensions recently, I don't know what's happening.  My gmail notifier is still reporting new messages, but I have to go to my other computer to actually see them.

Please help me[/QUOTE]
Have you tried running firefox in a terminal (Applications-->Accessories-->Terminal)? Just type
```
firefox
```
Then go to gmail. When it crashes, see if there's any error output or something. That might be a way of determining the problem.

---

### Post by ohzopants on 2006-02-28
At least now I get an error message and that's something to go on...

Anybody know what this means:
```
/opt/firefox/run-mozilla.sh: line 131: 10852 Segmentation fault      "$prog" ${1+"$@"}
```

---

