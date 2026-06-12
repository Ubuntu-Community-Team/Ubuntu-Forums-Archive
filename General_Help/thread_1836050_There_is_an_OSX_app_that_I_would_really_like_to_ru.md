---
title: "There is an OSX app that I would really like to run."
date: 2011-08-30
forum: General Help
---

### Post by ninjaaron on 2011-08-30
It's called Accordance.  It's professional-grade biblical studies software.  Anyway, they have a version that comes with a Windows emulator for OS 7.  The emulator also exists for Linux, but I can't get it to compile.  It works flawlessly WINE, so it's not a big deal.

Anyway, The OS 7 version of this software is, as one might well imagine, not quite as nice as the OSX version.  It is possible to run it in a virtual machine using the OSx86 builds.  I may or may not be obtaining those images at the moment. ;)

Is there a better solution, something like WINE, for OSX that doesn't require virutalization a and hacked up illegal software?

---

### Post by zero2xiii on 2011-08-30
A quick google turned up:

[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2007-November/002276.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2007-November/002276.html)

[https://help.ubuntu.com/community/SwitchingToUbuntu/FromMacOSX](https://help.ubuntu.com/community/SwitchingToUbuntu/FromMacOSX)

So it seems there is no "wine like emulator" for OSX. Either dual boot, oor virtualize. Maybe there have become alternatives availible, but I dont even see anything in the package manager that might help.

Good luck.

---

### Post by ninjaaron on 2011-08-30
Ok, few situation updates.  My hardware doesn't support virtualization (which usually isn't a problem with windows and *nix) so it won't run OSX in vm.  I was going to attempt to install it on a partition, and I had the installer up and running, but I was going to need to re-edit my partition table a little bit, so I went to the Ubuntu live CD.  I opened GParted and had an epiphany.

The program I want to use is exactly the same on the OS 7 Emulator as on OSX, just with less shiny.  It has all of the same features except for some 3D atlas thing (and it has flat maps that work fine).  I'm not going to install a massive operating system on another partition just to get a little extra shiny out of one program.

So I guess the thread is more or less 'solved,' but I'll leave it open in case anyone has a better solution than a full install of OSX.

---

