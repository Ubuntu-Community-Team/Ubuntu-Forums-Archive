---
title: "ld returned 1 exit status"
date: 2010-01-13
forum: General Help
---

### Post by shariefbe on 2010-01-13
Can anyone tell me what will be the error?
```
L  -lm -o corender
/mnt/freescale/toolchain/bin/../lib/gcc/arm-none-linux-gnueabi/4.4.1/../../../../arm-none-linux-gnueabi/bin/ld: warning: libX11.so.6, needed by ../../lib/libGL.so, not found (try using -rpath or -rpath-link)
/mnt/freescale/toolchain/bin/../lib/gcc/arm-none-linux-gnueabi/4.4.1/../../../../arm-none-linux-gnueabi/bin/ld: warning: libXext.so.6, needed by ../../lib/libGL.so, not found (try using -rpath or -rpath-link)
corender.o: In function `main':
corender.c:(.text+0x4c4): undefined reference to `XOpenDisplay'
corender.c:(.text+0x5d8): undefined reference to `XPending'
corender.c:(.text+0x5ec): undefined reference to `XNextEvent'
corender.c:(.text+0x614): undefined reference to `XLookupKeysym'
corender.c:(.text+0x634): undefined reference to `XLookupString'
corender.c:(.text+0x6e4): undefined reference to `XCreateColormap'
corender.c:(.text+0x740): undefined reference to `XCreateWindow'
corender.c:(.text+0x77c): undefined reference to `XSetNormalHints'
corender.c:(.text+0x7a4): undefined reference to `XSetStandardProperties'
corender.c:(.text+0x7d4): undefined reference to `XSetStandardProperties'
corender.c:(.text+0x7e0): undefined reference to `XMapWindow'
corender.c:(.text+0x868): undefined reference to `XChangeWindowAttributes'
../../lib/libGL.so: undefined reference to `XQueryExtension'
../../lib/libGL.so: undefined reference to `XQueryColors'
../../lib/libGL.so: undefined reference to `XFree'
../../lib/libGL.so: undefined reference to `XSetTile'
../../lib/libGL.so: undefined reference to `XCreateImage'
../../lib/libGL.so: undefined reference to `XQueryFont'
../../lib/libGL.so: undefined reference to `XUngrabPointer'
../../lib/libGL.so: undefined reference to `XGetWindowProperty'
../../lib/libGL.so: undefined reference to `XSetFillStyle'
../../lib/libGL.so: undefined reference to `XFreeColors'
../../lib/libGL.so: undefined reference to `dlsym'
../../lib/libGL.so: undefined reference to `XTranslateCoordinates'
../../lib/libGL.so: undefined reference to `XDrawPoint'
../../lib/libGL.so: undefined reference to `XCopyArea'
../../lib/libGL.so: undefined reference to `XSynchronize'
../../lib/libGL.so: undefined reference to `XDrawLine'
../../lib/libGL.so: undefined reference to `XFreeFontInfo'
../../lib/libGL.so: undefined reference to `XSetForeground'
../../lib/libGL.so: undefined reference to `XFillRectangle'
../../lib/libGL.so: undefined reference to `XShmCreateImage'
../../lib/libGL.so: undefined reference to `XGetGeometry'
../../lib/libGL.so: undefined reference to `XFreeGC'
../../lib/libGL.so: undefined reference to `XShmQueryVersion'
../../lib/libGL.so: undefined reference to `XSetFunction'
../../lib/libGL.so: undefined reference to `XSetLineAttributes'
../../lib/libGL.so: undefined reference to `XUngrabKeyboard'
../../lib/libGL.so: undefined reference to `XCreateGC'
../../lib/libGL.so: undefined reference to `XFlush'
../../lib/libGL.so: undefined reference to `XSync'
../../lib/libGL.so: undefined reference to `XPutImage'
../../lib/libGL.so: undefined reference to `XShmAttach'
../../lib/libGL.so: undefined reference to `XGetImage'
../../lib/libGL.so: undefined reference to `XAllocColor'
../../lib/libGL.so: undefined reference to `XSetPlaneMask'
../../lib/libGL.so: undefined reference to `XInternAtom'
../../lib/libGL.so: undefined reference to `XGetVisualInfo'
../../lib/libGL.so: undefined reference to `XAddExtension'
../../lib/libGL.so: undefined reference to `XGetWindowAttributes'
../../lib/libGL.so: undefined reference to `XShmPutImage'
../../lib/libGL.so: undefined reference to `XSetErrorHandler'
../../lib/libGL.so: undefined reference to `XFreePixmap'
../../lib/libGL.so: undefined reference to `XDrawString16'
../../lib/libGL.so: undefined reference to `XCreatePixmap'
../../lib/libGL.so: undefined reference to `dlopen'
../../lib/libGL.so: undefined reference to `XShmDetach'
../../lib/libGL.so: undefined reference to `dlclose'
collect2: ld returned 1 exit status
make[2]: *** [corender] Error 1
make[2]: Leaving directory `/mnt/freescale/sources/mesa-7.6/progs/xdemos'
make[1]: *** [subdirs] Error 1
make[1]: Leaving directory `/mnt/freescale/sources/mesa-7.6/progs'
make: *** [default] Error 1
Building  of glib library  has failed 
sharief@sharief-desktop:/mnt/freescale/sources/mesa-7.6$ 

```

---

