---
title: "Trouble w/ iMac 400 (slot loading): No X"
date: 2005-01-29
forum: General Help
---

### Post by jfitzmyer on 2005-01-29
I tried to install the latest Live CD, 5.04. The installation went fine until the very end and the only thing I have is a dark screen. Any suggestions?

---

### Post by menu on 2005-02-05
Same trouble here:

 Machine Model:	iMac tray loading (G3)
  CPU Speed:	267 MHz
Display
  Bus:	PCI
  Slot:	ATI
  VRAM (Total):	6 MB
  Vendor:	ATI (0x1002)
  Device ID:	0x4750
  Revision ID:	0x005c
  ROM Revision:	XXX-XXXXX-107

And allso no X on my girlfriends Imac:

iMac slotloading 350 MHz
  Opstart-ROM-versie:	4.1.9f1
  Serienummer:	SG9472CBHTM
 display AGP ATI 8 MB

On my G4 with an ATI 8500 the PPC livecd x resolution is locked to 640x480

So i guess there is something wrong with the way the ppc livecd detects apple hardware : (

---

### Post by jjramsey on 2005-02-05
Does anything in [this bug report](https://bugzilla.ubuntu.com/show_bug.cgi?id=4297) look familiar?

---

### Post by menu on 2005-02-05
[QUOTE=jjramsey]Does anything in [this bug report](https://bugzilla.ubuntu.com/show_bug.cgi?id=4297) look familiar?[/QUOTE]

i don't know really, the bug  you are linking to is :
Bugzilla Bug 4297
Can't start anymore X.org on an eMac (Radeon 7500)
Status:RESOLVED

We have Imacs, not Emacs, and my g4 has a Radeon 8500, so it might not be bug 4297
And the status is resolved, that means the problem is fixed no?

---

### Post by jjramsey on 2005-02-06
[QUOTE=menu]i don't know really, the bug  you are linking to is :
Bugzilla Bug 4297
Can't start anymore X.org on an eMac (Radeon 7500)
Status:RESOLVED

We have Imacs, not Emacs, and my g4 has a Radeon 8500, so it might not be bug 4297
And the status is resolved, that means the problem is fixed no?[/QUOTE]

No, it was marked RESOLVED because the bug is a duplicate. (Also, I believe the problem is an upstream bug with Xorg rather than with Ubuntu proper.) The bug hit me when I was trying out the LiveCD, so it is very much a current problem.

Just check if anything in your logs from Xorg looks like something in the bug report, especially stuff relating to DDC (monitor probing) and the hsync and vrefresh ranges that Xorg thinks your monitor has. It may or may not be related, but it's worth a look.

---

### Post by menu on 2005-02-07
[QUOTE=jjramsey]Just check if anything in your logs from Xorg looks like something in the bug report, especially stuff relating to DDC (monitor probing) and the hsync and vrefresh ranges that Xorg thinks your monitor has. It may or may not be related, but it's worth a look.[/QUOTE] 
Sorry but i am way to much a newbie for this. 

I just discovered that the PPC live cd release is not really "official" since it is not on the normal ubuntu download page so perhaps  my expectations were a bit to high.

I downloaded the latest version (7 feb 2005) and it will boot higher resolutions now on my G4 (only on 60 hz) but on my Imac it still gives a black screen and a  glowing yellow power button. If i press ctrl-alt-backspace than i hear a "ploeink" sound and the power button becomes green for a while but the screen stays black.

guess ill just have to wait patiently, i think ubuntu is a really nice operating system and i am looking forward to trying it on my Imac

---

