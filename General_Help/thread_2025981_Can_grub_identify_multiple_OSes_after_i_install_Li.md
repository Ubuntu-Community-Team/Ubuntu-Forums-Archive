---
title: "Can grub identify multiple OSes after i install Linux?"
date: 2012-07-14
forum: General Help
---

### Post by pavelexpertov on 2012-07-14
Basically, i am trying to have windows 7, win xp and Ubuntu 12.04. I believe that the grub can identify windows 7 after the ubuntu is installed, but can it detect mutiple OSes than one?

---

### Post by GreatDanton on 2012-07-14
Yes it can. I have 4 different Linux distributions, and Windows 7 on the same Hard disk.

---

### Post by oldfred on 2012-07-14
If you have two different versions of Windows that is different. Windows can only boot from the one primary NTFS partition that has the boot flag. So a second install of Windows moves all its boot files to that partition and has no boot files for grub to find.

If you have installed both Windows to primary partitions you may be able to repair the second install (or readd its boot files.)

To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by pavelexpertov on 2012-07-17
Thanks guys for info, I will do a little experiment next week and i will post the results and make the thread solved.

---

### Post by StormeRider on 2012-07-17
Doesn't Grub have an option to "hide" drives for this very purpose? So you can set up one drive with Win 7, one drive with Win XP, flag them both as active, and set whichever one is primary to be hidden when you want to boot the other?

---

