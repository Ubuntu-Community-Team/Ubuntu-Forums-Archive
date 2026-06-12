---
title: "Linux-Windows DualBoot using seperate HDs"
date: 2009-08-12
forum: General Help
---

### Post by ngrieb on 2009-08-12
I have just installed Windows on a second HD (currently slave) for gaming. I wanted to configure grub so that this Windows HD is bootable, but grub currently does not show up when I boot my computer. I have never dual-booted or used grub before, so I don't know where to start.

I know that the HD I am using right now (w/ Ubuntu 8.10 installed) is dev/sda1, and the Windows HD is dev/sdb1, but I don't recall how to check which HD (hd0,1...blah) is the current or how to setup grub using the /boot/grub/menu.list file. If you have done this before I would really appreciate any comments. Thanks.

---

### Post by dcstar on 2009-08-12
> **ngrieb said:**
> I have just installed Windows on a second HD (currently slave) for gaming. I wanted to configure grub so that this Windows HD is bootable, but grub currently does not show up when I boot my computer. I have never dual-booted or used grub before, so I don't know where to start.

I know that the HD I am using right now (w/ Ubuntu 8.10 installed) is dev/sda1, and the Windows HD is dev/sdb1, but I don't recall how to check which HD (hd0,1...blah) is the current or how to setup grub using the /boot/grub/menu.list file. If you have done this before I would really appreciate any comments. Thanks.

If you set up Grub on the second HD then you have to go into your BIOS and set it to boot off that disk.

You can also do a forum search on reinstalling/restoring Grub.

---

### Post by ngrieb on 2009-08-12
Well I wanted Ubuntu to be my master drive after all this is done, and I'm pretty sure grub is already installed. I just need some info on how to edit the /boot/grub/menu.list file so that Windows thinks it's the main HD, and how to configure the HD boot order in my BIOS.

---

### Post by ngrieb on 2009-08-13
I have found that grub gets overridden by Windows 7. How do I keep this from happening? I am booting off of (hd0, 0) my Ubuntu drive...but :( .

---

### Post by Moop on 2009-08-13
I don't think windows 7 will overwrite grub when you install it to a different harddrive. If you're booting off hd0 then grub is working. 

To edit boot ```
sudo gedit /boot/grub/menu.lst
``` and try adding this to the bottom.
```
 # on /dev/sdb
title Windows 7
root (hd1,0)
savedefault
makeactive
chainloader +1 
```If (hd1,0) doesn't work change it to (hd1,1)

---

### Post by ngrieb on 2009-10-01
Grub was screwing up the Widows 7 boot record, because I installed Windows 7 without my Linux drive being plugged in, and therefore Windows had no Idea there was another HD or OS around.

---

### Post by Rotax on 2009-10-01
Thought you may like sharing. In a month ago I have purchased SATA Drive switch cable. They has 3 separate cable for each drive and up to 3 drives. It can run each drive and has own master drive. I has 3 hard drives install on 1 system but all 3 are master drives. 1 are Window XP, I don't want Linux install that Window XP so I install Linux on other drive, and these Ubuntu are in 2nd drive and plan to install Fedora Project dual boot on 2nd drive. 
Now I have 3rd drive that is blank. I am thinking maybe try Window 7 or other Linux install in other 3rd drive. That way 1st drive will not touch Linux system. Here you can buy cable for  $32.00  or you can build cable for yourself, they has instruction on how to make cable. That way save your neck has to reinstall Window Xp in case bad grub booter may screwing up. 
[http://www.thesataswitch.com/](http://www.thesataswitch.com/)

---

