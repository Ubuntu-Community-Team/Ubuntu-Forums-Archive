---
title: "can't compile tuxnes"
date: 2006-03-29
forum: General Help
---

### Post by Zyphrexi on 2006-03-29
I want to run tuxnes/gtuxnes because I can't configure my gamepad to work with fceu, and i want a gui, but it won't compile. I think i have all the stuff, like build-essential. What do i do?

---

### Post by professor_chaos on 2006-03-29
start by reading the README file if there is one.

usually compiling is something like...

./configure
make
make install

do a search in the forum for more..

---

### Post by motin on 2008-01-18
Yes that's what's stated in the readme file. The compile error I get is:

```
$ ./configure
creating cache ./config.cache
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... yes
checking for working aclocal... found
checking for working autoconf... found
checking for working automake... found
checking for working autoheader... missing
checking for working makeinfo... found
checking host system type... configure: error: can not guess host type; you must specify one
```

Any ideas of how to do that?

---

