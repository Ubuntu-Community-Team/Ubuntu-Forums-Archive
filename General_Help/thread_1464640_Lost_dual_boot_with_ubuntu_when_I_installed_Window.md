---
title: "Lost dual boot with ubuntu when I installed Windows 7"
date: 2010-04-28
forum: General Help
---

### Post by Titchi707 on 2010-04-28
Hi, I am still new to Ubuntu and Linux. I had Ubuntu dual boot installed with Windows Vista and enjoyed using it. Then I upgraded Windows Vista (which was absolutely terrible) to Windows 7 (not clean install).
The dual boot disappeared, so that I could just load Windows 7. I would like to be able to get at my Ubuntu partition and have tried some live linux versions including the next and latest Ubuntu. It does not seem very satisfactory. I could re-install Ubuntu in the same partition, but this is messy, may result in loss of data and programmes and it still seems to be there anyway, but not accessible. How can I get my original Ubuntu back whilst retaining Windows 7? Ubuntu has only changed one version since the original installation.
Many thanks  David.

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by limey_rick on 2010-04-28
So when you upgraded to windows 7, it over wrote the MBR of the disk, where the boot loader is located, so GRUB does not come up now when you boot. 

What you need to do now is to follow these steps to re-install GRUB so that it will offer you a choice of what to boot when you turn on the PC. 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

If you have two disk drives, make sure you install GRUB in the one that the BIOS sees as first. If you only have one disk then you don't need to worry about this.

---

### Post by dino99 on 2010-04-28
you can boot with a cd and then chroot into the installed lucid following the example: [http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

then into console: sudo grub-mkconfig && update-grub

---

### Post by inso_741 on 2010-04-29
there are a lot of threads on dual-boot already....
but you have received the solution already....
just dont forget to mark this thread [solved]:popcorn:

---

### Post by humhook on 2010-04-29
HI my brother you can install the "grub4dos" pls google it oye!

---

