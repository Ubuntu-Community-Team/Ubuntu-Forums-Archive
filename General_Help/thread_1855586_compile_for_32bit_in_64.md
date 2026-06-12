---
title: "compile for 32bit in 64"
date: 2011-10-06
forum: General Help
---

### Post by johndebian on 2011-10-06
When i compile my source (cd into the directory, then make) i get a 64bit binary that works fine, because im on 64bit.

How would i compile my source to get a 32bit binary while im on a 64bit?
Do i have to get on a 32bit pc just to compile to get a .i386 binary?

---

### Post by noah++ on 2011-10-06
[FONT=Verdana]First couple Google hits got me[/FONT]
[FONT=Fixedsys]
export CFLAGS=-m32[/FONT]

or
[FONT=Fixedsys]
gcc -m32 -o helloprogram hello.c[/FONT]

---

