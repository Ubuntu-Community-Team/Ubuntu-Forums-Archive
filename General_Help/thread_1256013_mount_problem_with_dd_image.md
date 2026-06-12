---
title: "mount problem with dd image"
date: 2009-09-02
forum: General Help
---

### Post by DigOne on 2009-09-02
Hi,
  I'm currently running into a problem when using the mount command to attempt to mount a partition inside a dd image that I took of a hard drive.  Running parted on the net.img file shows that I have the following partitions:


```

root@caine-desktop:/mnt/big/# parted net.img unit B print
Model:  (file)
Disk /mnt/usb/Net_Case/net.img: 80026361856B
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start         End           Size          Type      File system  Flags
 1      32256B        10487231999B  10487199744B  primary   ntfs         boot
 2      10487232000B  80015523839B  69528291840B  extended               lba
 5      10487264256B  41940702719B  31453438464B  logical   fat32
 6      41940734976B  80015523839B  38074788864B  logical   ntfs

```
[LIST]
[*]I can then mount both partition #1 and #5 using mount -o loop,ro,offset=....
[/LIST]

[LIST]
[*]   However, when I attempt to do so using offset=41940734976, mount takes up 100% of the CPU and doesn't mount it.  Here's the full command: mount -o loop,ro,offset=41940734976 net.img /mnt/E
[/LIST]

[LIST]
[*]   Running strace on the mount command shows the following:
[/LIST]
 
```

ioctl(3, 0x4c03, 0xbfe75114)            = -1 EOVERFLOW (Value too large for defined data type)
close(3)                                = 0
open("/mnt/usb/Net_Case/net.img", O_RDONLY|O_LARGEFILE) = 3
open("/dev/loop1", O_RDONLY|O_LARGEFILE) = 4
readlink("/mnt", 0xbfe73057, 4096)      = -1 EINVAL (Invalid argument)
readlink("/mnt/usb", 0xbfe73057, 4096)  = -1 EINVAL (Invalid argument)
readlink("/mnt/usb/Net_Case", 0xbfe73057, 4096) = -1 EINVAL (Invalid argument)
readlink("/mnt/usb/Net_Case/net.img", 0xbfe73057, 4096) = -1 EINVAL (Invalid argument)
ioctl(4, 0x4c00, 0x3)                   = -1 EBUSY (Device or resource busy)
close(4)                                = 0
close(3)                                = 0
stat64("/dev", {st_mode=S_IFDIR|0755, st_size=4460, ...}) = 0
stat64("/dev/loop", 0xbfe751ec)         = -1 ENOENT (No such file or directory)
stat64("/dev/loop0", {st_mode=S_IFBLK|0660, st_rdev=makedev(7, 0), ...}) = 0
open("/dev/loop0", O_RDONLY|O_LARGEFILE) = 3
ioctl(3, 0x4c03, 0xbfe75114)            = 0
close(3)                                = 0
stat64("/dev/loop1", {st_mode=S_IFBLK|0660, st_rdev=makedev(7, 1), ...}) = 0
open("/dev/loop1", O_RDONLY|O_LARGEFILE) = 3
ioctl(3, 0x4c03, 0xbfe75114)            = -1 EOVERFLOW (Value too large for defined data type)
...

```  Any ideas?  Thanks.

---

### Post by DigOne on 2009-09-02
I forgot to mention that this is under Ubuntu 9.04 (Jaunty) with kernel 2.6.28-15-generic

```

root@desktop:/# lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 9.04
Release:        9.04
Codename:       jaunty

root@desktop:/# apt-cache policy mount
mount:
  Installed: 2.14.2-1ubuntu4
  Candidate: 2.14.2-1ubuntu4

root@desktop:/# uname -a

Linux desktop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux


```

---

