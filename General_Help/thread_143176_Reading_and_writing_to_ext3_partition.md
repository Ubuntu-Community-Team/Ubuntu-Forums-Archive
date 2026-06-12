---
title: "Reading and writing to ext3 partition"
date: 2006-03-11
forum: General Help
---

### Post by cabber on 2006-03-11
I recently partitioned a large drive into a FAT32 (100g) and an ext3 (100g).  Both are  showing up fine on the desktop.  The problem is that I can read and write to the FAT32, but cannot do anything with the ext3 drive.  I go into the properties of the drive and it states I am not the owner.  I've tried to create a "new" folder within the drive, and the option is greyed out.  This is my first ext3 drive so I am looking for help as to store data on the drive.  Please advise on what I am missing.  Thanks.

By the way, I am referring to using this drive while in the Ubuntu OS...not WIndows.  I believe there are drivers I would need to access this drive via WIndows.

---

### Post by xmastree on 2006-03-12
It will be in the way it's mounted. Are you mounting it manually? Or is it listed in /etc/fstab?
Post your /etc/fstab here and we'll be able to see the problem.

---

### Post by cabber on 2006-03-12
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30400   244187968+   7  HPFS/NTFS

Disk /dev/sdb: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       10397    83513871    c  W95 FAT32 (LBA)
/dev/sdb2           10398       14652    34178287+  83  Linux
/dev/sdb3           14653       48641   273016642+   f  W95 Ext'd (LBA)
/dev/sdb5           14653       14774      979933+  82  Linux swap / Solaris
/dev/sdb6           14775       39837   201318516    b  W95 FAT32
/dev/sdb7           39838       48641    70718098+  83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes


```

---

### Post by cabber on 2006-03-12
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults        0       0
/dev/sdb1       /media/sdb1     reiserfs defaults        0       2
/dev/sdb5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdb6       /media/LinuxXP  vfat   iocharset=utf8,umask=0000   0   0
/dev/sdb7       /media/LinEXT3  ext3   defaults   0   0
```

---

### Post by ILikeLinux on 2006-03-12
One simple way to solve this will be to change the ownership
of the directory /media/LinEXT3. If you want that only you
(as the user) can acess these files then change the ownership
of /media/LinEXT3, by 

```
sudo chown -R user.group /media/LinEXT3

```
where the user would be your user name, and the group would
be your default group, generally same as your user name. You
can first try :

```

cd $HOME
ls -l ../

```

There you will see the first your user name, then your default group.
These are the two things you should put in above. Hope this helps

---

