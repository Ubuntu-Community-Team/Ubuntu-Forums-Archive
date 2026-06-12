---
title: "Grub 2 being overwritten by Windows bootloader"
date: 2010-02-03
forum: General Help
---

### Post by oldtraveler on 2010-02-03
I have a dual boot system between Windows 7 and Ubuntu. When I install Ubuntu or restore Grub 2 from the Ubuntu disk, upon re-boot the Grub 2 screen appears and I select my choice.  But once I select the boot into Windows, then all re-boots after that do not show the Grub 2 screen but only the Windows boot up. Apparently the Windows boot is overwriting Grub 2. I wish to keep Grub 2 as my primary bootloader.

This has been an intermittent problem.  Today I have reinstalled the grub2 twice.  It will work as long as I boot to Ubuntu.  As soon as I boot to Windows 7, then all subsequent boots go to Windows 7 thus bypassing the grub 2 options.

---

### Post by Leppie on 2010-02-04
if this issue is solved, set the thread to solved using the thread tools.

---

### Post by oldtraveler on 2010-02-11
> **Leppie said:**
> if this issue is solved, set the thread to solved using the thread tools.
Unfortunately the problem continues.

---

### Post by Leppie on 2010-02-11
if you have a dell or hp, check this: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

---

