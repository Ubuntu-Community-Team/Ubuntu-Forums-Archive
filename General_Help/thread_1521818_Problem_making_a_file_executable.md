---
title: "Problem making a file executable"
date: 2010-07-01
forum: General Help
---

### Post by krishnamohan on 2010-07-01
I have a file which I wanted to make executable. It contains a sed script and was downloaded from a site.

It starts with 

**#!/bin/sh**


I changed the name from test.sed to test as instructed.
Used ***chmod +x**** test*** as well as ***chmod 777*** ***test*** on the file..

But  the command

***test <oldfile >newfile***

does not work..says command test not found....

---

### Post by gzarkadas on 2010-07-01
Put a ./ in front of test, to tell the shell it is in the current directory (it is *not* searched by default).

---

### Post by krishnamohan on 2010-07-06
Yes..that did it..thanks..:)

---

