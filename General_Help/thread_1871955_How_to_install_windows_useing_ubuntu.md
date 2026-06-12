---
title: "How to install windows useing ubuntu"
date: 2011-10-29
forum: General Help
---

### Post by devRinOkumura on 2011-10-29
Hello to all!
I'm new user thats my first post. Ofc like new user i have lots of questions but more of them have allrdy answers here. But there is one question who i'm fighting with from 1 month and still i didnt solve it. That's why i start that Thread.
Here is it.
I buy server machine HP Proliant DL380G3
[http://h18000.www1.hp.com/products/quickspecs/11473_div/11473_div.html](http://h18000.www1.hp.com/products/quickspecs/11473_div/11473_div.html) <--- here is specification from HP website.
i made bootable cd and installed ubuntu 10.04 LTS but now i want to change my os to windows 7
the problem is that i don't have DVD divice and i can't find one. i try lots of ways to install it under the ubuntu but all of them fail ... the windows can't find my HDD ... the error i get is "The Windows cannot find a location to store temporary installation files. To install Windows, make sure that a partition on your boot disk has at least 683 megabytes (MB) of free space. Error code: 0x800700490" ... also i tryed to install windows xp from bootable cd useing F6 and istalling drivers for SCSI ... but still error. so here is my question i just don't want to use other 1 month ... Can i install windows 7 or xp or 2008 server useing ubuntu LTS live cd. and if i can please give me some clues...

(i tryed install windows 7 from live cd ubuntu lts here is how i try:
1 i used Gparted to format with ntfs the disk space i wanted to use for windows 7
2 download Windows 7 ultiamte september iso file extract it and running setup exe useing WINE
still get that error 0x800700490)

So please if someone know how can i did that post here :) and 10x to all who give me from they time to read my crap.

---

### Post by LinuxFan999 on 2011-10-29
> **devRinOkumura said:**
> Hello to all!
I'm new user thats my first post. Ofc like new user i have lots of questions but more of them have allrdy answers here. But there is one question who i'm fighting with from 1 month and still i didnt solve it. That's why i start that Thread.
Here is it.
I buy server machine HP Proliant DL380G3
[http://h18000.www1.hp.com/products/quickspecs/11473_div/11473_div.html](http://h18000.www1.hp.com/products/quickspecs/11473_div/11473_div.html) <--- here is specification from HP website.
i made bootable cd and installed ubuntu 10.04 LTS but now i want to change my os to windows 7
the problem is that i don't have DVD divice and i can't find one. i try lots of ways to install it under the ubuntu but all of them fail ... the windows can't find my HDD ... the error i get is "The Windows cannot find a location to store temporary installation files. To install Windows, make sure that a partition on your boot disk has at least 683 megabytes (MB) of free space. Error code: 0x800700490" ... also i tryed to install windows xp from bootable cd useing F6 and istalling drivers for SCSI ... but still error. so here is my question i just don't want to use other 1 month ... Can i install windows 7 or xp or 2008 server useing ubuntu LTS live cd. and if i can please give me some clues...
 
(i tryed install windows 7 from live cd ubuntu lts here is how i try:
1 i used Gparted to format with ntfs the disk space i wanted to use for windows 7
2 download Windows 7 ultiamte september iso file extract it and running setup exe useing WINE
still get that error 0x800700490)
 
So please if someone know how can i did that post here :) and 10x to all who give me from they time to read my crap.
You can't run setup.exe in wine. Just burn the iso to a DVD, then reboot with the DVD inserted to install Windows 7.
 
By the way, I have 2 questions.
1. Why don't you want to use Ubuntu on your server?
2. If you really want to use Windows as a server OS, why didn't you get Windows Server 2008 R2 instead of Windows 7?

---

### Post by devRinOkumura on 2011-10-29
> **LinuxFan999 said:**
> You can't run setup.exe in wine. Just burn the iso to a DVD, then reboot with the DVD inserted to install Windows 7.
 
By the way, I have 2 questions.
1. Why don't you want to use Ubuntu on your server?
2. If you really want to use Windows as a server OS, why didn't you get Windows Server 2008 R2 instead of Windows 7?

First i can run setup in wine -> setup run i see window but when i klick install now ... it's says the error ... i post.
Second i don't have DVD Disk Drive and i can't find ... i have only CD
And i have ubuntu on my laptop ... on that machine i want to use win7 to test something ... but i can't install it ... anyway tnx for fast answer.

---

### Post by LinuxFan999 on 2011-10-29
> **devRinOkumura said:**
> First i can run setup in wine -> setup run i see window but when i klick install now ... it's says the error ... i post.
Second i don't have DVD Disk Drive and i can't find ... i have only CD
And i have ubuntu on my laptop ... on that machine i want to use win7 to test something ... but i can't install it ... anyway tnx for fast answer.
Keep in mand that you can't format/delete the root, boot, swap, and home partitions of a running Linux system, so installing Windows through Linux is not possible.
You can try booting and installing Windows from a USB flash drive.
use this guide: 
[http://arstechnica.com/business/news/2009/12/-the-usb-flash-drive.ars](http://arstechnica.com/business/news/2009/12/-the-usb-flash-drive.ars)
 
You will need to run the Utility in Wine.

---

### Post by critin on 2011-10-29
Go to the microsoft forums and ask about Error code: 0x800700490.  They will know for sure.

---

### Post by devRinOkumura on 2011-10-29
now i'm trying by other way ... with grub 
in 4 stebs 
1. download iso and extact it in allrdy made partition from live cd of ubuntu formated to ntfs 
2. installing grub
3. change MBR
4. reboot and boot from grub
i hope that work 
i open for other ways for dualbooting etc... 
ps: i don't need virtual way installed windows 7 with virtualbox or etc...

ps: LinuxFan999 i can't boot from usb flash.

---

### Post by oldtimer7777 on 2011-10-29
> **devRinOkumura said:**
> now i'm trying by other way ... with grub 
in 4 stebs 
1. download iso and extact it in allrdy made partition from live cd of ubuntu formated to ntfs 
2. installing grub
3. change MBR
4. reboot and boot from grub
i hope that work 
i open for other ways for dualbooting etc... 
ps: i don't need virtual way installed windows 7 with virtualbox or etc...

ps: LinuxFan999 i can't boot from usb flash.

Best way would be to use a disc of Ubuntu 11.10..   Use gparted..  Wipe your hard drive clean..  Install Windows from Disc.. Then Ubuntu.. Shrink the partition to 50/50 in comparable size.  Then you can Dual Boot both systems from Grub..  If you need to do data migration, do it before you wipe the system.

---

### Post by devRinOkumura on 2011-10-29
> **oldtimer7777 said:**
> Best way would be to use a disc of Ubuntu 11.10..   Use gparted..  Wipe your hard drive clean..  Install Windows from Disc.. Then Ubuntu.. Shrink the partition to 50/50 in comparable size.  Then you can Dual Boot both systems from Grub..  If you need to do data migration, do it before you wipe the system.

as i say in my first post i don't have DVD disk drive and i can't find one.

---

