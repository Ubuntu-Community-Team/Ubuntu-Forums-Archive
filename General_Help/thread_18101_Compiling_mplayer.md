---
title: "Compiling mplayer"
date: 2005-03-04
forum: General Help
---

### Post by ibs on 2005-03-04
When i try to compile mplayer i get this error:

```

ma -L/usr/X11R6/lib -lXext -lX11 -lnsl -lnsl        -L/usr/lib -ldl -lartsc -lpthread -lgmodule-2.0 -ldl -lgthread-2.0 -lglib-2.0 -L/usr/lib -lesd -laudiofile -lm  -laudio -lXt -L/usr/X11R6/lib -lXext -lX11 -lnsl       -lpthread -ldl -rdynamic   -lm
/usr/lib/libGL.a(glxcmds.o)(.text+0x2eea): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeQueryVersion'
/usr/lib/libGL.a(glxcmds.o)(.text+0x2f1a): In function `glXGetMscRateOML':
: undefined reference to `XF86VidModeGetModeLine'
collect2: ld returned 1 exit status
make: *** [mplayer] Error 1
ibs@ibs:~/MyDownloads/MPlayer-1.0pre6a $

```

What's wrong?

---

### Post by darrenadams on 2005-03-04
Do you have the libxxf86vm1 package (and maybe its corresponding development package, libxxf86vm-dev) installed? The function being referred to resides in those packages

---

