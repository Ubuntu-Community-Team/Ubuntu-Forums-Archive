---
title: "Bootloader problem"
date: 2011-07-18
forum: General Help
---

### Post by navcomstar on 2011-07-18
Have win 7 on one drive and ubuntu on 2nd drive then son goes and deletes partition that Ubi was in ,now cannot access any system all i get is grub rescue on screen and i cannot boot with any thing taking a guess the grub bootloader has died and made a mess of the windows bootloader 
Anyone help thankyou

---

### Post by dino99 on 2011-07-18
boot on livecd, then: sudo grub-install /dev/sda

---

### Post by Blasphemist on 2011-07-18
This shows Grub2 troubleshooting including preparation and booting from the grub> or grubrescue> prompts. [https://help.ubuntu.com/community/Grub2#GRUB](https://help.ubuntu.com/community/Grub2#GRUB) 2 Troubleshooting Preparation

What to do depends on your need. Doing what dino described is not going to get your partition back that was deleted. Nor is booting from the grub or grubrescue prompts. I'd use fixparts or testdisk or the system rescue cd or some other tool to recover the partition.
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by srs5694 on 2011-07-18
If the partition to which Ubuntu (and GRUB) was installed has been deleted, then re-installing GRUB won't work. In that situation, you'll need to use [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) to recover the partition. (FixParts won't do anything useful here, although it can fix a problem that TestDisk itself sometimes creates.)

If you need more advice, download and run [Boot Info Script](http://sourceforge.net/projects/bootinfoscript/) from an emergency disc and post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags to keep it legible.

---

