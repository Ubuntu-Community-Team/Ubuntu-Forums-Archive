---
title: "help needed - GRUB loading Error 17"
date: 2010-09-15
forum: General Help
---

### Post by viakal-fizz on 2010-09-15
Hello,

I have been running a partition on my HP Pavilion dv5 laptop for about a year now.

I had problems accessing wifi connections through the Ubuntu operating system which I couldn't resolve and ended up using the Vista operating system more. 1 year on, all my current files are on the Vista part of the partition and i never access Ubuntu (I know...I want to use Ubuntu over MS but this is the way it happened).

Anyway, I accessed the disk manager in vista and deleted the Ubuntu partition (this was the primary partition). On rebooting I am now confronted with:

GRUB loading stage1.5. 

GRUB loading, please wait...
Error 17

I know this has something to do with the Ubuntu partition being primary and the boot order being messed up. How do I resolve this issue? Could i reboot with ubuntu off a CD?

I've read a few forums that suggest booting up with DSL on a pendrive...what do you think???

Any help would be much appreciated. Thanks...

---

### Post by spiky001 on 2010-09-15
you have to rebuild the mbr with the vista disc

---

### Post by Rubi1200 on 2010-09-15
As spiky001 points out, you need to reinstall the Windows bootloader.

This link will tell you how to do that:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Scroll down to the relevant section.

Good luck!

---

