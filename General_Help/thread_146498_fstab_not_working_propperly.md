---
title: "fstab not working propperly??"
date: 2006-03-18
forum: General Help
---

### Post by JamesNorris on 2006-03-18
I seem t ohave a problem with write access to /mnt/win_c which is a fat32 partition with my old windows stuff on it. 
I have chmod-ed it to rwx for all users, and my fstab line is listed below
```
/dev/hda1       /mnt/win_c      vfat    umask=0000      0       0
```
I have tried adding uid=1000 which is my userid, but it didn't help either.

Any ideas what I'm doing wrong?

---

### Post by aysiu on 2006-03-18
Can you post the output of this command? ```
sudo fdisk -l
```

---

### Post by JamesNorris on 2006-03-18
Here ya go:
> Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161    c  W95 FAT32 (LBA)

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       30090    15165328+   f  W95 Ext'd (LBA)
/dev/hdb2           30091      155056    62982864    7  HPFS/NTFS
/dev/hdb5   *           1       14303     7208649   83  Linux
/dev/hdb6           14304       18959     2346592+  82  Linux swap / Solaris
/dev/hdb7           18960       30090     5609992+  83  Linux

---

### Post by aysiu on 2006-03-18
Sometimes the /mnt and /media folders do strange things when you mount partitions to them (don't ask me why).

Try this: ```
sudo umount /mnt/win_c
sudo mkdir /win_c
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` Replace this line ```
/dev/hda1       /mnt/win_c      vfat    umask=0000      0       0
``` with this line ```
/dev/hda1       /win_c      vfat    iocharset=utf8,umask=000      0       0
``` Save and then ```
sudo mount -a
```

P.S. You can't *chown* or *chmod* Windows partitions. It's all about the umask for permissions.

---

### Post by JamesNorris on 2006-03-18
Hmmmm That seemed to work. Why did it not work before when it was in /mnt then?

---

### Post by aysiu on 2006-03-18
[QUOTE=JamesNorris]Hmmmm That seemed to work. Why did it not work before when it was in /mnt then?[/QUOTE] I really don't know, but I do know that the /mnt and /media directories are special, and that's why I encourage folks to mount to a static folder outside of those two.

---

