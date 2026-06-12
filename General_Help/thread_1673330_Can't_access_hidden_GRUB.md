---
title: "Can't access hidden GRUB"
date: 2011-01-22
forum: General Help
---

### Post by Tsun on 2011-01-22
Once upon a time i hid the boot loader by setting the default boot to windows 7 and the waiting time to 0.  However, i can't seem to access it anymore... When i hold shift on boot, nothing happens. When i hold esc, my computer starts beeping like mad if i hold it too soon, but if i hold it later, it just goes to the windows boot thing and reboots.  So.. is there anything i can do other than downloading the whole OS again and making a live CD? (don't have the old one anymore)

---

### Post by Minn3h on 2011-01-22
I know of no other way to get to it. And it's always a good idea to have an extra live CD around, might as well start downloading now!

---

### Post by ronnielsen1 on 2011-01-22
Lots of options. You don't say what version of Ubuntu you hid but the earlier ones use grub and the later ones grub2

Restore grub:
[http://www.sorgonet.com/linux/grubrestore/](http://www.sorgonet.com/linux/grubrestore/)

Restore Grub2:
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

grub4dos: (can do from windows w/o having to download a live cd)
> **1).Using grub4dos**
First download grub4dos from [here]("http://download.gna.org/grub4dos/").
**1. ***For XP user*,copy the file “grldr”(without quotes) from grub4dos package to *C:\*.Edit *boot.ini* (hidden file in C:\) and add this line to the file:
 c:\grldr="grub4dos" *For Vista/win7 user*,copy the file “grldr”,”grldr.mbr” to *C:\*.Create boot.ini file in the root directory of C:,copy and paste following into this file.
 [boot loader]
timeout=0
default=c:\grldr.mbr
[operating systems]
C:\grldr.mbr="Grub4Dos" **2.** Now,create *menu.lst* in root directory of C:,its content:
 timeout 0
default 0
title grub2
find --set-root /boot/grub/core.img
kernel /boot/grub/core.img
boot Restart computer,and select boot from *Grub4Dos*.Then select boot up Ubuntu in grub menu.
Once login,use this command to install grub into mbr:
 sudo grub-install /dev/sda 

Plop boot manager:
[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

---

### Post by Tsun on 2011-01-22
I didn't take it to my dorm because i didn't know i'd need it :P And i'm trying to avoid downloading it because the file is huge and my internet connection is slow.   Edit: Installed Ubuntu when 10.04 was somewhat new. Also thanks ronnielsen1, i'll try those :)

---

### Post by ronnielsen1 on 2011-01-22
> And i'm trying to avoid downloading it because the file is huge and my  internet connection is slow.   Edit: Installed linux when 10.04 was  somewhat new. Also thanks ronnielsen1, i'll try thoseThen grub4dos or plop boot manager are probably your best bet. They're not real big. Shame on you for banishing Ubuntu to the netherlands of your computer;)

---

