---
title: "ok to delete duplicate of root?"
date: 2009-08-07
forum: General Help
---

### Post by joshstl79 on 2009-08-07
Hi.  Thanks for reading.

Anyway, obviously i'm new, but i have a serious question maybe you can help me with.  When i installed ubuntu on my box, i set it up with 4 partitions (used GParted).  I'm guessing that i screwed something up though, because i have what appears to be a duplication of my root files on more than one partition.

[SIZE="2"]root@josh-laptop:/media/disk-2# ls
bin    etc             lib         opt   srv       tmp      vmlinuz.old
boot   home            lost+found  proc  sys       usr
cdrom  initrd.img      media       root  testdir   var
dev    initrd.img.old  mnt         sbin  tftpboot  vmlinuz


root@josh-laptop:/# ls
bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv      usr  vmlinuz.old[/SIZE]

I made up a directory titled "testdir" on the disk-2 partition to make sure that i wasnt crazy...

It's not a huge deal i guess, but it *is* taking up about 7 Gig of space, at least from what i can tell.  

SO my questions: [1] if i delete this stuff on my other partition will it screw up my system, and [2] assuming it wont screw things up, how do i do that?

Thanks for your help.

---

### Post by dcstar on 2009-08-07
> **joshstl79 said:**
> Hi.  Thanks for reading.

Anyway, obviously i'm new, but i have a serious question maybe you can help me with.  When i installed ubuntu on my box, i set it up with 4 partitions (used GParted).  I'm guessing that i screwed something up though, because i have what appears to be a duplication of my root files on more than one partition.

[SIZE="2"]root@josh-laptop:/media/disk-2# ls
bin    etc             lib         opt   srv       tmp      vmlinuz.old
boot   home            lost+found  proc  sys       usr
cdrom  initrd.img      media       root  testdir   var
dev    initrd.img.old  mnt         sbin  tftpboot  vmlinuz


root@josh-laptop:/# ls
bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv      usr  vmlinuz.old[/SIZE]

I made up a directory titled "testdir" on the disk-2 partition to make sure that i wasnt crazy...

It's not a huge deal i guess, but it *is* taking up about 7 Gig of space, at least from what i can tell.  

SO my questions: [1] if i delete this stuff on my other partition will it screw up my system, and [2] assuming it wont screw things up, how do i do that?

Thanks for your help.

Post the output of the following terminal commands:
```

sudo fdisk -l
cat /etc/fstab
```

---

### Post by joshstl79 on 2009-08-07
thanks for your quick reply... here's the output for each command

**sudo fdisk -l:**

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfcaff6ae

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9239    74212236   83  Linux
/dev/sda2            9240       30401   169983765    5  Extended
/dev/sda5           29672       30401     5863693+  82  Linux swap / Solaris
/dev/sda6            9240       14519    42411537   83  Linux
/dev/sda7           28942       29671     5863693+  82  Linux swap / Solaris
/dev/sda8           14520       21442    55608966    b  W95 FAT32
/dev/sda9           21443       28941    60235686    b  W95 FAT32

Partition table entries are not in disk order
Note: sector size is 4096 (not 512)

Disk /dev/sdb: 7952 MB, 7952142336 bytes
217 heads, 32 sectors/track, 279 cylinders
Units = cylinders of 6944 * 4096 = 28442624 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         280     7765508    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 32)
Partition 1 has different physical/logical endings:
     phys=(120, 216, 32) logical=(279, 126, 32)


**cat /etc/fstab:**

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=9acdb430-e58f-41d8-8fd5-d2ff93d7462d /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=2ef4feb1-2733-4e43-95fa-376d6ac285fd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

