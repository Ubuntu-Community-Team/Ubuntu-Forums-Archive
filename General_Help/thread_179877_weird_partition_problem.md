---
title: "weird partition problem"
date: 2006-05-20
forum: General Help
---

### Post by dccool879 on 2006-05-20
i had /dev/sda5 be deleted for windows to use. then i reboot back into ubuntu and all my partitions are messed up. by messed up, for example, my /dev/sda6 became /dev/sda11, so now my /dev/sda6 thinks its /dev/sda11 as a swap partition. how can i get this back to normal?? its supposed to be a shared ntfs with my mp3's to share between OS's.

---

### Post by aysiu on 2006-05-20
Do you have a live CD?

---

### Post by dccool879 on 2006-05-20
no but i could burn it. but i dont need it because i can still boot into ubuntu right??  (because /dev/sda1 stayed /dev/sda1)

---

### Post by aysiu on 2006-05-21
[QUOTE=dccool879]no but i could burn it. but i dont need it because i can still boot into ubuntu right??  (because /dev/sda1 stayed /dev/sda1)[/QUOTE] Oh! Yeah, if you can boot into Ubuntu, you probably don't need it. It wouldn't hurt to have one, just in case (for future use).

So boot into Ubuntu, and post the output of these commands here: ```
cat /etc/fstab
sudo fdisk -l
df -h
```

---

### Post by dccool879 on 2006-05-21
haro@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda11      none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda6       /media/share ntfs users,owner,ro,umask=000 0 0
/dev/sda5       /media/sh     ext3    defaults        0       0
haro@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9729    78148161   83  Linux
omitting empty partition (5)

Disk /dev/sda: 160.0 GB, 160041885696 bytes
16 heads, 63 sectors/track, 310101 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       69795    35176648+  83  Linux
/dev/sda2           69796      310101   121114224    5  Extended
/dev/sda5           69796       72819     1524033   82  Linux swap / Solaris
/dev/sda6           72820      112541    20019856+   e  W95 FAT16 (LBA)
/dev/sda7          112542      123242     5393272+  83  Linux
/dev/sda8          123243      123779      270616+  82  Linux swap / Solaris
/dev/sda9          123780      134690     5499112+  83  Linux
/dev/sda10         134691      135235      274648+  82  Linux swap / Solaris
/dev/sda11         135236      310101    88132432+   7  HPFS/NTFS
haro@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              34G   31G  1.4G  96% /
tmpfs                 507M     0  507M   0% /dev/shm
/dev/hda1              74G   53G   18G  75% /media/music
haro@ubuntu:~$

---

### Post by aysiu on 2006-05-21
You probably know your partitions better than I do, but I'd guess this would work: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/sda1 / ext3 defaults,errors=remount-ro 0 1
/dev/sda5 none swap sw 0 0
/dev/hdd /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdc /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/sda11 /media/share ntfs users,owner,ro,umask=000 0 0
/dev/sda7 /media/sh ext3 defaults 0 0
```

---

