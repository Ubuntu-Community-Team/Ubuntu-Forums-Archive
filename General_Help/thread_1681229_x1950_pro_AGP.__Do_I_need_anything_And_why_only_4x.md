---
title: "x1950 pro AGP.  Do I need anything? And why only 4x AGP?"
date: 2011-02-03
forum: General Help
---

### Post by tominto on 2011-02-03
Hey guys, I just installed an ATI x1950 pro (which I had previously been using on a windows installation)  Do I need any extra drivers, or configuration to get it to work at it's best.  I'm currently using it with whatever came with meerkat.  

And can someone please tell me why I can't get it to work at it's intended 8x?  It's an 8x AGP graphics card, and I'm using it on a board that supports 8x...but it only runs at 4x.

Relevant info from dmesg:

agpgart: Detected VIA KM400/KM400A chipset

agpgart-via 0000:00:00.0: AGP 3.5 bridge
[   19.757219] agpgart-via 0000:00:00.0: putting AGP V3 device into 4x mode
[   19.757297] radeon 0000:01:00.0: putting AGP V3 device into 4x mode

---

### Post by tominto on 2011-02-05
Ok, I figured the answer to part of my problem.  The open source drivers are already installed, and I can expect problems if I install the proprietary ATI ones.  So I'll stay with xorg then, although I found a modified version of them (xorg-edgers) which I've installed.  

However I still can't figure out why I can't get my graphics card to run at 8x AGP.  I've done some research, and tried disabling KMS through grub.  This had the effect of very high frame rates in glxgears, but graphics were incredibly choppy in a few games I tried.  So that wasn't the solution.  Also tried adding an option to xorg.conf to put AGP to 8x, and didn't appear to work (unless I did something wrong)  Still get "putting AGP V3 device into 4x mode" in either of these cases.

Anyone have any ideas?  I'd like to have it running at it's intended 8x.

---

### Post by tominto on 2011-02-08
Anyone?

---

