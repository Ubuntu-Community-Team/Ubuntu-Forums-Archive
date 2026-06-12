---
title: "USB Stick formatting help"
date: 2012-07-04
forum: General Help
---

### Post by yttriuszzerbus on 2012-07-04
I have a 2GB USB stick from a while ago, which came as two partitions: a ~1.98GB main, encrypted partition and a ~2MB partition containing the decryption software. I don't need the encryption, and I've since disabled it. However, I can't seem to merge the partitions. Windows XP shows it as E:\ and F:\ as I expected, so I figured I'd use Ubuntu and that it would show up as /dev/sdb1 and /dev/sdb2, meaning I could use dd if=/dev/urandom of=/dev/sdb to completely erase it and format it from there. But when I put it in, it came up as /dev/sdb and /dev/sdc. Is there anything I can do about this, or are the partitions separated by the drive itself?
Thanks,
yttriuszzerbus

---

### Post by msammels on 2012-07-04
Have you tried installing gparted and using that to partition your drive?

---

### Post by cortman on 2012-07-04
GParted is the easiest way to tweak partitions. With only the flash drive plugged in, run

```
sudo fdisk -l
```

and post the output here. Also, do you have more than one HDD in your computer?

---

### Post by efflandt on 2012-07-04
It would help if you said what kind it is.  If it is a Sandisk with U3, the other drive is sort of a pseudo cdrom on the stick.  Web search "sandisk u3 removal".

BTW I heard that Windows only sees 1 partition on USB flash memory, so maybe appearing as 2 devices gets around that.

---

### Post by yttriuszzerbus on 2012-07-04
Gparted shows in the menu in the top-right of the window a choice of /dev/sda (my only hard drive, internal), /dev/sdb (The 1MB partition) and /dev/sdc (The 2GB partition).
sudo fdisk -l returns:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders, total 488281250 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       96389       48163+  de  Dell Utility
/dev/sda2   *       96390   307777738   153840674+   7  HPFS/NTFS/exFAT
/dev/sda3       481950000   488247479     3148740   db  CP/M / CTOS / ...
/dev/sda4       307779582   481949695    87085057    5  Extended
/dev/sda5       307779584   474771455    83495936   83  Linux
/dev/sda6       474773504   481949695     3588096   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1 MB, 1048576 bytes
1 heads, 2 sectors/track, 1024 cylinders, total 2048 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?   778135908  1919645538   570754815+  72  Unknown
/dev/sdb2   ?   168689522  2104717761   968014120   65  Novell Netware 386
/dev/sdb3   ?  1869881465  3805909656   968014096   79  Unknown
/dev/sdb4   ?           0  3637226495  1818613248    d  Unknown

Partition table entries are not in disk order

Disk /dev/sdc: 2062 MB, 2062548992 bytes
64 heads, 62 sectors/track, 1015 cylinders, total 4028416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   ?   778135908  1919645538   570754815+  72  Unknown
/dev/sdc2   ?   168689522  2104717761   968014120   65  Novell Netware 386
/dev/sdc3   ?  1869881465  3805909656   968014096   79  Unknown
/dev/sdc4   ?  2885681152  2885736650       27749+   d  Unknown

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

```
This is on a live CD, so none are mounted. It's an Integral brand memory stick from some years ago, so it's unlikely to be U3, but I'll give the remover program a try.
yttriuszzerbus

---

### Post by cortman on 2012-07-04
> **yttriuszzerbus said:**
> Gparted shows in the menu in the top-right of the window a choice of /dev/sda (my only hard drive, internal), /dev/sdb (The 1MB partition) and /dev/sdc (The 2GB partition).
sudo fdisk -l returns:

This is on a live CD, so none are mounted. It's an Integral brand memory stick from some years ago, so it's unlikely to be U3, but I'll give the remover program a try.
yttriuszzerbus

I'd just go ahead and wipe /sdb and /sdc with GParted; also see [this thread]("http://ubuntu.5.n6.nabble.com/Reformatting-a-USB-stick-that-shows-up-as-two-devices-td1569080.html") for apropos information.

---

