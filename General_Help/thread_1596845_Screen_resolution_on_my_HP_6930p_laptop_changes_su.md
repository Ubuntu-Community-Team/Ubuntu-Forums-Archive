---
title: "Screen resolution on my HP 6930p laptop changes suddenly"
date: 2010-10-14
forum: General Help
---

### Post by Daan on 2010-10-14
Hi,

The screen resolution on my HP 6930p laptop changes often suddenly to lower than native. I most times I can set it back, but sometimes it fails and a pop up appears telling me "could not set the configuration for crtc 64".

/log/var/Xorg.0.log then gets these lines added:

```
(II) intel(0): Modeline "1280x800"x0.0   69.32  1280 1292 1356 1416  800 803 806 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 19522
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   69.32  1280 1292 1356 1416  800 803 806 816 -hsync -vsync (49.0 kHz)
(II) intel(0): Allocate new frame buffer 1872x768 stride 1920
(II) intel(0): EDID vendor "SEC", prod id 19522
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   69.32  1280 1292 1356 1416  800 803 806 816 -hsync -vsync (49.0 kHz)
(II) intel(0): Allocate new frame buffer 1024x768 stride 1024
(II) intel(0): EDID vendor "SEC", prod id 19522
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   69.32  1280 1292 1356 1416  800 803 806 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 19522
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   69.32  1280 1292 1356 1416  800 803 806 816 -hsync -vsync (49.0 kHz)
(II) intel(0): EDID vendor "SEC", prod id 19522
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x800"x0.0   69.32  1280 1292 1356 1416  800 803 806 816 -hsync -vsync (49.0 kHz)
(II) intel(0): Allocate new frame buffer 1280x800 stride 1280
(II) AIGLX: Suspending AIGLX clients for VT switch
```

Anny suggestions?

---

