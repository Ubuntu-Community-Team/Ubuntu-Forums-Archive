---
title: "How to build an exectuable package from my source code"
date: 2006-03-27
forum: General Help
---

### Post by Roobert on 2006-03-27
Hi,

Yeah I have some source code that I want to make into a binary executable with an installation script as well. Most source code I download comes in the form of a shell script for installation and a tar.gz package. How do I make these from the source code up?

Thanks,

Roobert.

---

### Post by Leif on 2006-03-27
Depends on what language you use to a certain extent I guess, but look up make/makefile.

---

### Post by taurus on 2006-03-27
Normally when you download something that you need to build for your machine, you just unpack it with tar command and then change to that new directory.  Then, read the README and/or INSTALL for instructions but the whole thing would look something like
```

tar xvzf <filename>.tar.gz
-or-
tar xvjf <filename>tar.bz
cd <filename>
./configure
make
sudo make install

```

---

