---
title: "Ati 4870 with Dual Monitor problem"
date: 2009-07-21
forum: General Help
---

### Post by bperucchi on 2009-07-21
I'm to two week try to use my ATI 4870 with dual view with two monitors and this time I quite. Unfortunately I'm going back two use Windows 7. I need to work with two monitor.

I try to use Flgrx the last version I didn't work
I try to use Ati Catalasty for ATI Drivers didn't work
I try to use Xinerma didn't work

And already test the Ubuntu 8.04(32and64), 8.10(32and64), 9.04(32and64), 9.10(32and64), 9.10-Karmic(32and64)

Yes, I installed 10 distribution in 3 days and I already test Fedora,Suse,Debian

I made many configuration in the xorg.conf.

This is Xorg.0.log
Backtrace:
0: /usr/X11R6/bin/X(xorg_backtrace+0x26) [0x4f1e96]
1: /usr/X11R6/bin/X(xf86SigHandler+0x41) [0x48b671]
2: /lib/libc.so.6 [0x7ff357e56040]
3: /usr/X11R6/bin/X(RRCrtcGammaSet+0x1e) [0x51e10e]
4: /usr/lib/xorg/modules/drivers//fglrx_drv.so [0x7ff355cf1105]
5: /usr/X11R6/bin/X [0x48cd52]
6: /usr/X11R6/bin/X [0x48ce88]
7: /usr/X11R6/bin/X(xf86HandleColormaps+0x281) [0x48de81]
8: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayScreenColormapSetup+0x79) [0x7ff355cf0869]
9: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxDisplayScrnInit+0x137) [0x7ff355ced6a7]
10: /usr/lib/xorg/modules/drivers//fglrx_drv.so(atiddxScreenInit+0x791) [0x7ff355cadbc1]
11: /usr/X11R6/bin/X(AddScreen+0x1c6) [0x433616]
12: /usr/X11R6/bin/X(InitOutput+0x241) [0x46efe1]
13: /usr/X11R6/bin/X(main+0x20e) [0x433d2e]
14: /lib/libc.so.6(__libc_start_main+0xe6) [0x7ff357e415a6]
15: /usr/X11R6/bin/X [0x433369]
Saw signal 11.  Server aborting.
(II) Screen 0 shares mem & io resources
(II) Screen 1 shares mem & io resources
 ddxSigGiveUp: Closing log

---

