---
title: "Grub 2 corrupted by AutoCAD"
date: 2010-03-05
forum: General Help
---

### Post by Vind on 2010-03-05
Hi all,

I run my computer with two operating systems on one i have Ubutnu 9.10 on the other win7. I have been using both OS without a single problem until now.

I very recently installed AutoCAD 2010 on my win partition and for some reason that is out of my grasp every time i use ACAD it seems to corrupt/overwrite the Grub2 launching partition.

If I use ACAD next time I restart the PC the Grub2 menu list of OS does not appear and the PC just restarts over and over. I do not encounter any problems if I use win partition without running ACAD.

I find myself having to reinstall grub2 from a Ubuntu live sesion every time I use ACAD.

Any information as why this might be happening and a way to avoid it would be greatly appreciated.

Thank you all in advance,

Vind

---

### Post by darolu on 2010-03-05
This is very weird; did you install Ubuntu with Wubi?

---

### Post by Vind on 2010-03-05
Installation was done in the following order:

-Installed win7 using all the HD
-Downloaded Ubuntu 9.10 burned it on a CD and installed using the CD, specifying partition size with the slider.

Always done it this way and it has never given me any problems. I am totally blown as why ACAD has the capability of modifying the boot partition myself.

---

### Post by oldfred on 2010-03-05
Grub2 is larger than grub and windows boot loaders. It turns out some windows software used the tiny extra space to write serial numbers or other info. Also some virus checkers see a non-windows boot loader and corrupt the boot loader.
Is this another software hiding info in the boot sector?

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)

---

### Post by Vind on 2010-03-05
Hi Oldfred,

I have briefly read through some links you have kindly forwarded and sounds as though this version of CAD behaves in the same way as the software your links speak about. I will look into the links with more attention tomorrow morning, and tell you what the outcome is.

Thank you for your time and information,

Vind.

---

### Post by XEtedBear on 2010-12-28
> **Vind said:**
> Hi Oldfred,

I have briefly read through some links you have kindly forwarded and sounds as though this version of CAD behaves in the same way as the software your links speak about. I will look into the links with more attention tomorrow morning, and tell you what the outcome is.

Thank you for your time and information,

Vind.

Sorry to wake this up again after so long. I just fell into the same hole - it took me 36 hours to finally recover my system. I do want to be able to use AutoCAD on my dual-boot system - but not at the cost of having to re-install GRUB each time.

Did you find a good work-around to this problem?

---

### Post by oldfred on 2010-12-28
It looks like the newest versions of grub have a work around for flexnet. This user posted what grub returned.

[http://ubuntuforums.org/showthread.php?t=1654510](http://ubuntuforums.org/showthread.php?t=1654510)

Best case with software that absolutely has to control the MBR and boot sectors is just to spend the $50 for another hard drive and separate Ubuntu from Windows.

---

