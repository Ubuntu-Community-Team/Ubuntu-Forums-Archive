---
title: "/usr/bin/ld: cannot find -lXtst"
date: 2006-04-16
forum: General Help
---

### Post by gregleimbeck on 2006-04-16
I am trying to install kxdocker, it seems to go fine.  I ran these commands:

sudo ./configure
sudo make
sudo make install

When I run the make install it errors out, giving me "/usr/bin/ld: cannot find -lXtst
" What is lXtst?  I can't find anything about it for ubuntu.  This must be something simple, I just have no idea what I am supposed to do.

Thanks in advance.

---

### Post by babalou on 2006-04-16
I had the same problem with gxine.
What I did to bypass the problem was editing Makefile and src/Makefile files and updated LDFLAGS entry to:
LDFLAGS = -L/usr/X11R6/lib

then everything went fine.

yb

---

### Post by Kebabji on 2006-04-18
download libxtst headers from adept

---

### Post by chaplinux on 2008-02-09
$ sudo aptitude install libxtst-dev

:guitar:

---

