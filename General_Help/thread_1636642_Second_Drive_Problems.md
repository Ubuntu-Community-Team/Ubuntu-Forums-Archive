---
title: "Second Drive Problems"
date: 2010-12-03
forum: General Help
---

### Post by Whisp3r on 2010-12-03
Hi everyone. I'm trying to add a second hard drive to my computer for the purposes of backing up by files before I make the upgrade from 9.04 to 10.10. 

I added a second SATA drive, which has become sda. I used gparted and made it FAT32 so my windows OS can use it (rare, but once anda while). 

sudo fdisk shows the following:

```

Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000792f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      182401  1465136001    b  W95 FAT32

```

I did a sudo mount /dev/sda1 /media/drive2, and it shows up under my /media folder. I then sudo mount the drive, it appears on my desk top and I can view it. 

I then do the following:
sudo chown -R myusername:myusername /media/drive2, which results in: 
```

chown: changing ownership of `/media/drive2': Operation not permitted

```

What am I doing wrong?

---

### Post by Whisp3r on 2010-12-03
A quick update.

When I right click on it running nautilus under gksudo mode, it says file permissions cannot be determined.

When I tried to format it at Fat32, it only took about 15 seconds to format an entire 1.5 TB drive. What is wrong here? Any help is greatly appreciated. I expected more of a problem with upgrading to 10.10, then installing a simple drive. :P

---

### Post by efflandt on 2010-12-03
2 potential issues trying to back up files to FAT32.  It has no concept of file permissions, who owns a file, whether it should be allowed to execute, etc..  And it is limited to 4 GB file size.

You can possibly get around the first issue by using tar or other archive method to preserve ownership, permissions, etc.  But if you end up with too much data in one file, that backup file may exceed the 4 GB limit.  Even Win7 would refuse to backup to a FAT32 file system.

So if you may end up with larger files (like DVD isos) that you want to be accessible to Windows, it would be better to use NTFS.  Any Windows version XP or newer should be able to access that (not sure about Win98/ME).

---

