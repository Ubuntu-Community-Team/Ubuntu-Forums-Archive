---
title: "External Drive Stuck as Read-Only"
date: 2010-12-04
forum: General Help
---

### Post by jlbr on 2010-12-04
Hi, I've got an WD external drive, formatted as FAT, which strangely enough, has gotten stuck as Read-Only, I say strange because it was working fine before. Now I can't read or write anything to it. Anyway, I have tried the chown command, chmod, I added this line to the fstab:

/dev/sr1 none udf rw,noauto 0 0

This is because some post I read said this would stop the drive from mounting as sr1 and thus avoid some WD proprietary software thing. Anyhow, I'm tired of fidgeting around, I'm not literate enough in Ubuntu to fix this, and I'm afraid of doing more damage than help. I really need to back up some work, please help.
I am posting my fdisk -l:

> juanluis@juanluis-laptop /etc $ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x77b277b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1245    10000431   83  Linux
/dev/sda2            1246       38913   302568210    5  Extended
/dev/sda5            1246        1369      995998+  83  Linux
/dev/sda6            1370        1742     2996091   82  Linux swap / Solaris
/dev/sda7            1743       38913   298576026   83  Linux

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)


Thanks a lot in advance. By the way, I have Karmic Koala as my present system, 64 bit.

---

### Post by drs305 on 2010-12-04
First, make a mount point. If you want to see it on your desktop, put it in /media. If not, put it in /mnt. For the example, I'll use /mnt/mydrive. Change it to anything you want:

```
sudo mkdir /mnt/mydrive
sudo chown -R $USER: /mnt/mydrive  # Make yourself the owner. Leave $USER: as is.
sudo blkid  # Find the UUID for /dev/sdb1
gksu gedit /etc/fstab  # Open fstab for editing
```

For now, change  your fstab setting to the following:
> /dev/sdb1 /mnt/mydrive vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0
Save the file and run the following:
```
sudo mount -a
``` 
If Ubuntu is happy with your fstab entry, you won't see anything but your drive will now be mounted and available on /mnt/mydrive.

You can substitute the UUID found for /dev/sdb1 for /dev/sdb1 in the fstab line. It is a much better way to enter it. That entry would be:
> UUID=<the uuid from the blkid command> /mnt/mydrive vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0

Example:
UUID=8879vf-8498-fg466s  /mnt/mydrive vfat defaults,user,exec,uid=1000,gid=100,umask=000 0 0

Note: the reason the chmod and chown commands didn't work was that fat32 doesn't support Linux permissions. You can set the mount point permissions at the time of mounting but can't change them afterward. The settings in the fstab line allow you to do what you (and others) want with the files. You can read up on fstab permissions if you want to change the umask values.

---

### Post by jlbr on 2010-12-04
Thanks drs305, but the second command does not work as you can see:

> juanluis@juanluis-laptop ~ $ sudo chown -R juanluis $USER:mnt/"DRIVE 2" #juanluis
chown: cannot access `mnt/DRIVE 2': No such file or directory
juanluis@juanluis-laptop ~ $ cd /mnt
juanluis@juanluis-laptop /mnt $ ls
DRIVE 2

What's weird is that the drive also seems like it is mounted in /media, but it's not, and ther e are all those instances of the drive, which are not real:

> juanluis@juanluis-laptop /media $ ls
\012  cdrom  cdrom0  cdrom1  DRIVE2  DRIVE 2  DRIVE 2_
juanluis@juanluis-laptop /media $ ^C
juanluis@juanluis-laptop /media $ sudo umount /media/"DRIVE 2"
umount: /media/DRIVE 2: not mounted
juanluis@juanluis-laptop /media $ sudo umount /media/"DRIVE 2_"
juanluis@juanluis-laptop /media $ sudo umount /media/DRIVE2
umount: /media/DRIVE2: not mounted

What's the deal here??

---

### Post by drs305 on 2010-12-05
> **jlbr said:**
> Thanks drs305, but the second command does not work as you can see:

What's weird is that the drive also seems like it is mounted in /media, but it's not, and ther e are all those instances of the drive, which are not real:

What's the deal here??

> sudo chown -R juanluis $USER:mnt/DRIVE 2 #juanluis

The $USER is "juanluis", so you don't list them both. Also you forgot the / before "mnt". It is usually better to copy and paste commands rather than type them when possible.

Making your mount point a single word will make things much easier: DRIVE_2.

```

sudo chown -R juanluis: /mnt/DRIVE_2
or
sudo chown -R $USER: /mnt/DRIVE_2

```

---

