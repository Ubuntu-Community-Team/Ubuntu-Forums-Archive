---
title: "USB Hard drive won't load"
date: 2011-02-12
forum: General Help
---

### Post by calebi on 2011-02-12
I recently reinstalled Ubuntu 10.10 on my system. I then wanted to get rid of Windows 7 (which crashed and doesn't work) so I deleted the OS_Install partition that was on there. The tutorial I was reading told me to delete both Linux Swap partitions so I could take all the unallocated space and put it on one partition (/dev/sda2). So I did that.

At first everything worked great, then I ran like 250 updates that were listed and now it won't load my 250GB external hard drive which has all my files on it that were backed up from Windows. I don't know if this has anything to do with it, but my system won't boot with the drive pluged in and neither will my other Windows Vista system.

My first though was that it wasn't being recognized but when I ran lsusb it said it was there.
```

root@caleb-A6200:/home/caleb# lsusb
[COLOR="Red"]Bus 002 Device 006: ID 1058:0704 Western Digital Technologies, Inc. Passport External HDD[/COLOR]
Bus 002 Device 003: ID 13d3:5092 IMC Networks 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0cf2:6250 ENE Technology, Inc. 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

But when I run fdisk -l, it doesn't show up.
```

root@caleb-A6200:/home/caleb# fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000881ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1906    15307776   83  Linux
/dev/sda2   *       29953       60802   247795713    5  Extended
/dev/sda5           58201       60802    20888576   82  Linux swap / Solaris
/dev/sda6           29953       58201   226906112   83  Linux

Partition table entries are not in disk order

```

I'm not necessarily new to Ubuntu but I'm not advanced with it and I can't figure this out, any help would be awesome.

Thanks,
Caleb

---

### Post by mikewhatever on 2011-02-12
Could it be that you've deleted a couple of udev rules when browsing the file system as root?

---

### Post by calebi on 2011-02-12
I only thing I've deleted was one of the linux swaps and I did that using GParted that I installed.

---

### Post by calebi on 2011-02-12
I only thing I've deleted was one of the linux swaps and I did that using GParted that I installed.

---

### Post by wlambchop on 2011-05-02
I'm having exactly the same problem with a new installation of ubuntu 11.04. I have been reading other forums, it could be that a failure to disconnect the drive correctly from windows is to blame. I'm going to try opening it in windows and doing an error check + disconnection. I will let you know how that goes

---

