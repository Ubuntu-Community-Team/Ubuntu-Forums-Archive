---
title: "Newer versions of ubuntu don't work."
date: 2011-03-12
forum: General Help
---

### Post by panfist on 2011-03-12
The latest version of ubuntu that I can install on a certain machine is 9.10. Vanilla 9.10 works just fine as far as I can tell. If I upgrade to a newer version of itself, or 10.04, it does not work. I can select a newer kernel version in grub, then I get no signal to the monitor. If it's a newer recovery kernel, I can alt-sysreq-REISUB, but if it's not a recovery mode, then I can't even do that.

I have also tried the 10.04 and 10.10 live CDs and they don't work.

I'm using the 64-bit version.

---

### Post by ajgreeny on 2011-03-12
What hardware are you using?

I would suspect a video card problem that may be solved by using one of several possible kernel boot options that you may need to set, at least to start with, and then when you have the right driver for the card all may work OK.

Try the live CD, and when you get to the screen where you just see the purple screen with two icons at the bottom (a keyboard and a figure of a man) or when you get the option to Try ubuntu, Install ubuntu, etc etc, press F6 and try the **nomodeset** option.

---

### Post by panfist on 2011-03-13
I'm trying your suggestion now.

In the meantime, I can say that my hardware is an HP Pavilion a1600n, based on AMD X2 3800+ CPU (windsor I think), with integrated geforce 6150 LE.

Actually, it did manage to boot into the 10.10 live CD with **nomodeset**.

I did not suspect the graphics driver initially, because it is an old chipset from nvidia, widely used, and I thought nvidia's driver support was supposed to be pretty good.

I'm still not sure how to proceed. I'm assuming that if I want to install 10.10, I can do it from here, then reboot with nomodeset from my hard disk instead of the live cd, then install the proper driver. Trying that now...

---

### Post by ajgreeny on 2011-03-14
That's the way to do it normally, but keep us posted about success or failure.

---

