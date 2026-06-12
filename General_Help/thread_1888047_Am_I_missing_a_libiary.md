---
title: "Am I missing a libiary?"
date: 2011-11-28
forum: General Help
---

### Post by magpie03 on 2011-11-28
Hello all,
Trying to install EPhem in Ubuntu 10.10.
Following instructions I start by typing in terminal:

MOTIF=../../libXm/linux86

It runs then ends like this:

../../libXm/linux86/Xm/Xm.h:56: fatal error: X11/Intrinsic.h: No such file or directory
compilation terminated.
make: *** [aavso.o] Error 1

To test it I type ./xephem and get
magpie@magpie-desktop:~/Downloads/xephem-3.7.5/GUI/xephem$ ./xephem
bash: ./xephem: No such file or directory
or when I sudo it:
magpie@magpie-desktop:~/Downloads/xephem-3.7.5/GUI/xephem$ sudo ./xephem
sudo: ./xephem: command not found

Any ideas?
Many thanks all

I can post terminal output if needed.

Note I believe this is an old program

---

### Post by Ra'anan on 2011-11-28
hey magpie

try xlib-mesa and libxt-dev

you're probably missing xlib-mesa...

but there are also dev libs you may need:

libX11-devel-1.0.3-11.el5.i386
libXt-devel-1.0.2-3.1.fc6.i386

---

### Post by BC59 on 2011-11-28
You should run:

```
sudo dpkg --configure -a
sudo apt-get -f install
```

To ensure if all necessary packages are completely installed and configured.

---

### Post by magpie03 on 2011-11-29
Thank you very much all.
I'll try them today and let ya know.

---

