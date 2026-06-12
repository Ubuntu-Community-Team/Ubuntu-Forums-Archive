---
title: "Help me compile and build this program"
date: 2011-03-29
forum: General Help
---

### Post by cap10Ibraim on 2011-03-29
here are the files 
```

ibrahim@ibrahim-laptop:~/Desktop/1x/btscanner-1.0$ ls
bs_info.c    bs_sdp.c        configure     INSTALL      oui.txt
bs_scan.c    btscanner.c     configure.in  Makefile.in  README
bs_screen.c  btscanner.h.in  COPYING       ouidb.c

```

---

### Post by mc4man on 2011-03-29
There is a README and a configure - read the README and run the configure to see if it does so or shows what libraries you're missing

---

### Post by seawolf167 on 2011-03-29
Aye, get in a habit of reading the README file, if that doesn't explicitly tell you the procedures to install, you can always try the default

```
./configure
make
make install
```

Then depending on the errors thrown in the previous commands, you may need to resolve additional dependencies, etc.

---

