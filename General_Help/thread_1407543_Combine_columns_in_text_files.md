---
title: "Combine columns in text files"
date: 2010-02-15
forum: General Help
---

### Post by ixchel on 2010-02-15
Hi.

I have two files which I would like to combine. Each file has 2 columns.
File 1:
1 a
2 b 
3 c
File 2:
1 5
2 55
3 56

I tried:  paste File1 File2 > File3
and I get this:
1 a 1 5
2 b 2 55
3 c 3 56

In File 3 I would like to get this:
1 a 5
2 b 55
3 c 56


Is there any way to that with a linux command?

---

### Post by rnerwein on 2010-02-15
hi

paste pas pas1 | awk '{ printf" %s %s %s \n",$1,$4,$2}'

ciao

---

### Post by ixchel on 2010-02-15
Thanks  :D

---

