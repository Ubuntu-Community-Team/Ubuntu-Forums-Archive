---
title: "Grub Error"
date: 2010-01-26
forum: General Help
---

### Post by HACKER1993 on 2010-01-26
I am getting an error after the self boot sequence when after X minutes the system auto boots the highlighted option in my case it is mint 7 after that screen an error comes up with Random numbers and letters then Stuck?? anyone else had this on ubuntu?

---

### Post by ajgreeny on 2010-01-26
The random numbers could be the UUID of the partition that the system is trying to boot, which is perhaps incorrect.  If needed boot to the live CD and run in terminal the command
```
sudo blkid
``` and then try to mount the ubuntu hard disk partition and check either the /boot/grub/menu.lst file or /boot/grub/grub.cfg file, both of which should show your partition UUIDs, and will allow you to check that the numbers are the same as in blkid, and are also the same as those showing when your screen freezes at boot.

I have had a similar situation on my ubuntu 9.04 (the same as your Mint 7) where at boot occasionally my machine shows grub, then the UUID of the partition and then says "Starting up" but goes no further.  When it does boot properly it will quickly show "Loading, please wait" after that and all is well.  If mine freezes at that point, the reset button seems to get it running OK next time.  Other forums have suggested that I disable the fast boot in BIOS and let the system do the long check of ram, but with 2GB that takes a long time, so I have just set the grub timeout to a longet than my usual 3 secs to see if that helps.  They are suggesting it may be a power supply problem, or the disk being slow to spin up.

I'll keep looking into this and wait to see what you find.

---

