---
title: "ubuntu unresponsive but running on normal boot, runs fine on low graphics mode."
date: 2010-11-24
forum: General Help
---

### Post by amshank on 2010-11-24
Hi guys,

This started a few days ago and I checked back through recently installed packages and nothing looks related.

If I boot into ubuntu normally, plymouth looks a mess, but then things boot fine but while the mouse is showing and ubuntu goes about with connecting to networks and so on, but it doesn't register the and input from the mouse or keyboard. It will sleep if you press the power button, but its no more responsive after waking up.

If I boot into recovery mode, and use the failsafe graphics option then everything runs fine. Apart from 3D graphics being pretty slow, which I can kind of understand.

I get the same behaviour on all of the last three kernels.

I'm running the latest maverick on an HP 6715b. i386 version although the processor is 64 bit compatible. 2Gb RAM.

Anyone have any ideas for me to try or any extra info I should go looking for? I'm at a loss myself.

Thanks

---

### Post by amshank on 2010-11-25
I just had a look at my Xorg log and there are some wierd errors.

There's about 100 lines of;

....
[    47.429] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    47.429] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    47.429] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
[    47.429] (EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
....

and then near the end it gives up with;

...
[   378.820] (WW) xf86CloseConsole: KDSETMODE failed: Input/output error
[   378.820] (WW) xf86CloseConsole: VT_GETMODE failed: Input/output error
[   378.820] (WW) xf86OpenConsole: VT_GETSTATE failed: Input/output error
[   378.820] (WW) xf86CloseConsole: VT_ACTIVATE failed: Input/output error
[   378.820] (WW) xf86CloseConsole: VT_WAITACTIVE failed: Input/output error
[   378.820]  ddxSigGiveUp: Closing log



An input/output error feels like this might be related.
Anyone have any clues as to where to take it from here?

---

