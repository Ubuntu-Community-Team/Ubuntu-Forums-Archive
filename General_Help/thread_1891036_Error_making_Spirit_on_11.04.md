---
title: "Error making Spirit on 11.04"
date: 2011-12-04
forum: General Help
---

### Post by taunnt on 2011-12-04
Hello I'm having issues making Spirit, I get this error:


make
gcc -std=gnu99 -c -o spirit.o spirit.c
spirit.c:29:25: fatal error: plist/plist.h: No such file or directory
compilation terminated.
make: *** [spirit.o] Error 1

What install package am I missing?

---

### Post by jjex22 on 2011-12-04
Is this Spirit as in Jailbreaking?, I assume so as plist is an osx thing... Can't say I approve, that would be against forum rules, but when compiling software from source, it tells you about dependencies you are missing when you run ./configure -it'll be the last output :)

Edit: just checked their site - aparently it only works for certain firmwares, and there's an updated make file that could help :) [Here]("http://spiritjb.com/")

---

