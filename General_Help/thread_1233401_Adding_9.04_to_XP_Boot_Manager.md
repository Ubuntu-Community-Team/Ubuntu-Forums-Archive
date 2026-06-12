---
title: "Adding 9.04 to XP Boot Manager"
date: 2009-08-06
forum: General Help
---

### Post by Oyerth on 2009-08-06
Hello, all. I installed Ubuntu 9.04 on an external hard drive and elected to have GRUB not alter my MBR so that I can use the XP boot loader to choose between XP and Ubuntu. I followed [this]("http://dandar3.blogspot.com/2009/07/add-ubuntu-904-to-windows-xp-boot.html") guide to try and add Ubuntu to the boot list. I used the live cd to create the .bin file as it suggets and placed it on my C drive where the boot manager would have access to it. Again, following the guide, I added C:\ub.bin="Ubuntu" to boot.ini, saved, and restarted. When I choose "Ubuntu" from the boot list all I see is the word "GRUB" and continues to hang. During some research, I discovered that it could be the fact that my XP and Ubuntu partitions are on separate, physical disks. Is this assumption correct?

Is there any way I can accomplish this boot configuration? The reason I want to use the XP boot manager and not GRUB is because sometimes my external hard drive won't be connected to my desktop and don't really want to be dependant on it being connected to the desktop.

Any suggestions? Thanks. :)

---

### Post by P4man on 2009-08-07
Can your bios boot off your external drive ? If so, an easy solution is to have grub on your external drive, letting you chose windows and ubuntu, and keep XP bootloader on the internal. If the external isnt connected, your computer will just boot the internal one.

---

