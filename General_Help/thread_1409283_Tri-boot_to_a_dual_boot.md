---
title: "Tri-boot to a dual boot"
date: 2010-02-17
forum: General Help
---

### Post by SoFl W on 2010-02-17
I installed a dual boot with W2Kpro and openSUSE several years back and recently I installed ubuntu as a tri-boot.   I never really liked suse, didn't use it and probably wont use it.

I would like to reclaim the drive space but I believe the openSuse partition is the boot partition.  The areas that I want to delete and make into one partition look fragmented.   When I use System-Administration->Disk_Utility it says I have a free 10G area, I am not sure how.
I do have a Windows C and D drive. 

I would like to change this to a dual boot with ubuntu and windows, keeping the Windows partition and a small FAT32 storage partition, 500megs would be more than enough.   I would also like to create a separate /home partition.  Suse creates a separate home partition so I could delete the user folders, make that my home partition for ubuntu and move my files to that.

I am not sure where the boot partition is.  I am using grub2 now but it might have been placed with the old suse and I don't want to ruin my boot.

Any advice on what is the *easiest* way to reclaim space as one partition and create a separate or use the existing suse home directory for ubuntu?

**df -l**
```

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda7              9550756   3270408   5795188  37% /
udev                    509160       284    508876   1% /dev
none                    509160       184    508976   1% /dev/shm
none                    509160       288    508872   1% /var/run
none                    509160         0    509160   0% /var/lock
none                    509160         0    509160   0% /lib/init/rw
/dev/sda6              8238400    492048   7327868   7% /media/01180917-ae30-41e1-826e-f4ca366dfa25
```**fdisk -l**
```

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2056    16514788+   c  W95 FAT32 (LBA)
/dev/sda2            3649        7296    29302560    f  W95 Ext'd (LBA)
/dev/sda3            2057        2249     1542209   82  Linux swap / Solaris
/dev/sda4   *        2249        3648    11245499+  83  Linux
/dev/sda5            3649        3750      819283+   b  W95 FAT32
/dev/sda6            4987        6028     8369802   83  Linux
/dev/sda7            6029        7236     9703228+  83  Linux
/dev/sda8            7237        7296      481918+  82  Linux swap / Solaris

```
My DVD/CD does not work, I can use a bootable USB drive.

---

### Post by tom4everitt on 2010-02-17
Why don't you post the output of this script, it contains a lot of useful info concerning your boot:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by SoFl W on 2010-02-17
/dev/sda4 is suse and the boot partition
/dev/sda1 is the W2K partition

I am thinking it would just be easier to start over however I need to know if I backup my home folder, delete everything except for /dev/sda1, and do a fresh install will it automatically pick up the windows partition so I can keep the dual boot?  Is there anything on sda4 that lets the system know about Windows on sda1?

---

### Post by tom4everitt on 2010-02-18
Sure, I usually prefer to do it that way too. 

The only info about your windows xp that could be on your boot partition is in grubs config file: /boot/grub/menu.lst (you're probably using the old grub). If you want you can make a backup of that as well, just to be sure. 

Normally grub2, which is installed with ubuntu 9.10, will automatically discover your windows installation.

---

### Post by SoFl W on 2010-02-18
> **tom4everitt said:**
> 
Normally grub2, which is installed with ubuntu 9.10, will automatically discover your windows installation.

The DVD drive no longer works so I don't want to lose my W2K.  I will keep only the W2K partition and delete everything else, hopefully grub2 will pick it up. I will then try reinstalling off a USB stick.   I am going to keep it Tri-boot for a little while longer, isn't hurting anything and if it works why fix it?

---

### Post by tom4everitt on 2010-02-19
Haha, yeah. Personally I like "fixing" working things just because of the joy of fixing them again when they brake... I realize not everyone share my enthusiasm for broken software though :)

---

### Post by SoFl W on 2010-05-18
I ended up deleting the OpenSuse partitions, Ubuntu 9.10 and did a fresh install of 10.4.
I tried KDE, (kubuntu) and realized that is what I didn't like about my OpenSUSE install.   (It has been a few years since I played around with it)

---

