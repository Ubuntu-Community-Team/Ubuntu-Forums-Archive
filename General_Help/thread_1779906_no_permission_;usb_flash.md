---
title: "no permission ;usb flash"
date: 2011-06-11
forum: General Help
---

### Post by intelligence storm on 2011-06-11
hi every one,
i was writing on my flash and nothing is wrong
but yesterday i put my flash to write on some files ....it said no permission to write !!! so i can't either delete or add any file !!!
i googled the problem and tried many solution but no one worked !!
last on was here [http://ubuntuforums.org/showthread.php?t=1242310&highlight=write+permission+usb+flash](http://ubuntuforums.org/showthread.php?t=1242310&highlight=write+permission+usb+flash)
tried this code

> **Bradj47 said:**
> That worked for me:
```

brad@rockstar:~$ sudo chown -R brad:brad /dev/sdc
brad@rockstar:~$ sudo cat /usr/lib/syslinux/mbr.bin > /dev/sdc
brad@rockstar:~$ 

```Thanks!

:frown::frown::frown: i wish i didn't cos i can't see my flash anymore](*,)](*,)
please help without reformatting it
thanks in advance

---

### Post by TeoBigusGeekus on 2011-06-11
Can you post us the output of
```
sudo fdisk -l
```
-L

---

### Post by intelligence storm on 2011-06-11
[PHP]wisdom@wisdom-MS-1034:~$ fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x05720571

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3775    30322656    7  HPFS/NTFS
/dev/sda2            3776       14593    86895554+   f  W95 Ext'd (LBA)
/dev/sda5            3776       10150    51207156    b  W95 FAT32
/dev/sda6           10151       12445    18434556    b  W95 FAT32
/dev/sda7           12446       14593    17253778+  83  Linux
wisdom@wisdom-MS-1034:~$ 
[/PHP]

with or without plug the flash in?!! anyway either it is or not the output seems same

---

### Post by TeoBigusGeekus on 2011-06-11
Can you also post us the output of
```
lsusb
```
with and without the flash drive plugged in?

---

### Post by intelligence storm on 2011-06-11
1-without
[PHP]wisdom@wisdom-MS-1034:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15d9:0a41 Trust International B.V. MI-2540D [Optical mouse]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0db0:6877 Micro Star International RT2573
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/PHP]

2-with
[PHP]wisdom@wisdom-MS-1034:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 15d9:0a41 Trust International B.V. MI-2540D [Optical mouse]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 014: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 003: ID 0db0:6877 Micro Star International RT2573
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
wisdom@wisdom-MS-1034:~$ 
[/PHP]

---

### Post by TeoBigusGeekus on 2011-06-11
Your flash drive is recognized
```
Bus 001 Device 014: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
```
What's it's capacity? Are you sure it isn't one of the partitions listed with fdisk?

---

### Post by intelligence storm on 2011-06-11
its capacity is 4 Gb and i'm sure that is not listed in fdisk -l (i re-verify)
i said before that it doesn't appear anymore so i can't access !!!
but noticed in dev file ,two files appear when it's plugged named as :sdb & sdb1 ; with X at file corner -i'm still beginner so don't know what does it mean-

should i format my flash memory ??!! but how ??

---

### Post by TeoBigusGeekus on 2011-06-11
Fire up gparted
```
gksu gparted
```
and format it.
It's the only way to be sure...

---

### Post by intelligence storm on 2011-06-11
thank you for you serving 
i didn't wish to take this solution but no way!!
can you tell me a good application to recover my files

---

