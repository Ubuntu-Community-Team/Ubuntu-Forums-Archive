---
title: "X won't start for me on PPC"
date: 2005-02-04
forum: General Help
---

### Post by jjramsey on 2005-02-04
The LiveCD seems to be functional. (Filenames of .udebs are [truncated](http://www.ubuntuforums.org/showthread.php?t=13981), but that seems to be a red herring.) X refuses to start, however. This is on an eMac with ATi graphics.

X dies with the error message:

```

(EE) RADEON (0): FBIOPUT_VSCREENINFO: Invalid argument

Fatal server error: AddScreen/ScreenInit failed for driver 0

```

In the output of dmesg is the line

```

radeonfb: Invalid ROM signature 0 should be 0xaa55

```

The graphics card is detected as an ATi Radeon 7500. The monitor is detected as an "iMac", and its default hsync and vrefresh ranges are 28-33 kHz and 43-72 Hz, respectively. For comparison, on OS X, the actual refresh rate is 89 Hz.

Any ideas as to what is going wrong?

---

### Post by jjramsey on 2005-02-05
Figured out what's going on, more or less. I got bit by Ubuntu bug [4297](https://bugzilla.ubuntu.com/show_bug.cgi?id=4297).

---

