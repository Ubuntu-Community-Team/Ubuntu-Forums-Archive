---
title: "fixing broken partion table"
date: 2010-07-25
forum: General Help
---

### Post by sundays211 on 2010-07-25
as you can see in my attachment, I have a partion that is out of place (34gb ext3), under a 5.8gb extended partion container. is there any way to fix this without needing to format the drive (as that partion contains my /home files). I have a theory that this is also what is causing grub to fail to load, as it always comes up with a message about sda having no partions whenever I try to install it on /dev/sda.

thanks

---

### Post by oldfred on 2010-07-25
post this:
```

sudo fdisk -lu
```

If partitions were correct testdisk may be able to repair.

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
repairs including testdisk info & links
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)
Testdisk & photorec
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

### Post by sundays211 on 2010-07-26
the result of "sudo fdisk -lu":
```
ubuntu@ubuntu:~$ sudo fdisk -lu
Ignoring extra extended partition 2

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa7ea90c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    11261564     5630751   85  Linux extended
/dev/sda2        11261626    78156224    33447299+   5  Extended

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa660a660

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1         1044225    25912844    12434310   83  Linux
/dev/sdb2        25912906    78156224    26121659+   5  Extended
/dev/sdb3              63     1044224      522081   83  Linux
/dev/sdb5        25912908    26957069      522081   82  Linux swap / Solaris
/dev/sdb6        26957133    78156224    25599546   83  Linux

Partition table entries are not in disk order

```

---

### Post by sundays211 on 2010-07-26
thanks. using testdisk worked perfectly. I now have the disk partitions looking like they used to.  by fixing sda, I was also able to re-install grub and can now boot linux properly.
thanks again.

---

