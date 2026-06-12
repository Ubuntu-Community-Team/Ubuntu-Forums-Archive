---
title: "GRUB restarts"
date: 2010-05-04
forum: General Help
---

### Post by Deldo on 2010-05-04
Hey.

I installed Lucid Lynx some days ago. 
Whenever I try to acces Vista from GRUB, the computer restarts.
I haven't changed anything about how the computer starts.

Please help me.

Rune

---

### Post by dino99 on 2010-05-04
sudo grub-mkconfig && update-grub

hope you have not installed grub over windows bootloader, might be installed into lucid mbr partition

[http://ubuntuforums.org/showthread.php?t=1467891&page=2](http://ubuntuforums.org/showthread.php?t=1467891&page=2) post 14

---

### Post by oldfred on 2010-05-04
Most everyone that saw that screen read it wrong.

Fix for most, a few have other issues:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

This is what the instructions say (bold by me):
If you're unsure which **drive **is designated as boot drive by your BIOS, it is often a good idea to install GRUB to all of them.        

It also says:
Note: It is possible to install GRUB to **partition** boot records as well. However, this forces GRUB to use the blocklist mechanism, which makes it less reliable, and therefore is **not recommended**.

It then presents a check box with all** drives** and **partitions**. So everyone (And I think it its everyone) checks all the boxes. Only drives sda, sdb, etc should be checked. Not partitions sda1, sda2, sdb1, etc.

Installing to the windows partition overwrites part of the windows boot that is already in the windows boot sector or PBR.


[http://ubuntuforums.org/showthread.php?t=1471896&highlight=Vista](http://ubuntuforums.org/showthread.php?t=1471896&highlight=Vista)
[http://ubuntuforums.org/showthread.php?t=1464655&highlight=Vista](http://ubuntuforums.org/showthread.php?t=1464655&highlight=Vista)
[http://ubuntuforums.org/showthread.php?t=1469724&highlight=Vista](http://ubuntuforums.org/showthread.php?t=1469724&highlight=Vista)
[http://ubuntuforums.org/showthread.php?t=1466031&highlight=Vista](http://ubuntuforums.org/showthread.php?t=1466031&highlight=Vista)

---

### Post by Deldo on 2010-05-04
I tried your example. It didn't help.
As you said. I might have installed GRUB over the windows bootloader. I remember when I installed Lucid Lynx and GRUB 2, I chose every partitions. :-/

---

### Post by Deldo on 2010-05-04
Thank you. The sectors were not identical, but I fixed it with testdisk.

---

