---
title: "Windows boot loader doesn't detect keyboard"
date: 2010-01-04
forum: General Help
---

### Post by derkrampus on 2010-01-04
I know this might not be the best place for these questions, but since people here use Wubi, I thought someone may have encountered my situation.

I installed Ubuntu using Wubi, and the boot loader does not detect my keyboard.  Does the windows boot loader only support PS2 keyboards?  Would there be a workaround... like install DOS drivers for it?  I have a logitech s520 keyboard.

When in Windows, I can select what OS to use, but is there a way I can select which OS to use while booted into Ubuntu?  Is there a program that will let me modify the windows boot loader from within Ubuntu?

Thanks!!!
J

---

### Post by prshah on 2010-01-04
> **derkrampus said:**
> Does the windows boot loader only support PS2 keyboards?  Would there be a workaround...

You need to enable legacy support for USB keyboards/mice from your BIOS setup.

Enter your BIOS (typically, press Del during startup, or F2, or F10, though it differs from motherboard to motherboard).

Then look for any of the following options (or wording-combinations thereof): USB Legacy Support, USB Keyboard Support, Legacy USB, USB DOS support, etc. Enable it; it will not affect performance in Windows, Linux, etc. It will just enable keyboard functionality in non-USB HI OS's.

---

### Post by derkrampus on 2010-01-09
PRShah,

I had looked in CMOS but originally didn't see any relevant settings.  I must have been focused on the word keyboard and overlooked/didn't realize there was a setting for USB legacy support.   You're the man!!!

If you see me around, stop me because I definitely owe you a beer.

J

---

