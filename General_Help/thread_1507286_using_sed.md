---
title: "using sed"
date: 2010-06-11
forum: General Help
---

### Post by krishnamohan on 2010-06-11
Hi...

I wanted to use sed to break a big file into smaller chunks. Basically, I want it to scan the file, copy the portion between "start" and "stop" if it contains the string one 1 into file 1 and continue along copying portions between start and stop into files 1,2,3 etc depending on which string they contain.

I found somewhere how to copy the portion between two strings.

***sed -n '/And then/,/sapiens/p' sedtest>sedtest2***

should have read through sedtest and copied the portion between And then and sapiens to sedtest2. It does that, but also copies another line which begins with And then but with no sapiens anywhere in the file after that.

---

### Post by krishnamohan on 2010-07-08
[http://sed.sourceforge.net/sedfaq4.html](http://sed.sourceforge.net/sedfaq4.html)

**4.21. How do I delete or change a block of text if the block  contains a certain regular expression?**



By changing d to p and using sed -n, I was able to copy only sections containing a certain word...

---

