---
title: "Cannot compile dwm window manager"
date: 2011-09-13
forum: General Help
---

### Post by geo909 on 2011-09-13
Hello all,

I just downloaded the latest (5.9) version of the dwm window manager. When I am trying to compile it, though, I get the following:
```

jorge@Office-Desktop:~/Software/dwm-5.9$ sudo make clean install 
cleaning
dwm build options:
CFLAGS   = -std=c99 -pedantic -Wall -Os -I. -I/usr/include -I/usr/X11R6/include -DVERSION="5.9" -DXINERAMA
LDFLAGS  = -s -L/usr/lib -lc -L/usr/X11R6/lib -lX11 -L/usr/X11R6/lib -lXinerama
CC       = cc
CC dwm.c
dwm.c:40:37: fatal error: X11/extensions/Xinerama.h: No such file or directory
compilation terminated.
make: *** [dwm.o] Error 1


```

Does anybody have any idea why this happens? Any clue about what I should do?

Many thanks  in advance..

---

### Post by geo909 on 2011-09-13
Ah, I only had to comment out all the lines in config.mk
which were related to xinerama.. Now it works..

---

### Post by animeshb on 2013-02-21
> **geo909 said:**
> Ah, I only had to comment out all the lines in config.mk
which were related to xinerama.. Now it works..

Thanks this worked for me.

But, I think a better way is to just install libx11-dev and libxinerama-dev.

```
sudo apt-get install libx11-dev libxinerama-dev
```

---

