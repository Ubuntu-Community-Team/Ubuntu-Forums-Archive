---
title: "Installing Ubuntu on SD card for Beagle Board"
date: 2011-09-06
forum: General Help
---

### Post by bneva on 2011-09-06
I'm trying to follow these steps to install the OS onto my MicroSD card (4GB) but it doesn't seem to work.
[https://wiki.ubuntu.com/ARM/OmapNetbook](https://wiki.ubuntu.com/ARM/OmapNetbook)

I tried the first one which was
```
sudo sh -c 'zcat ./ubuntu-11.04-preinstalled-netbook-armel+omap.img.gz |dd bs=4M of=/dev/mmcblk ; sync'
```

error
```
dd: writing `/dev/mmcblk': No space left on device
0+31822 records in
0+31821 records out
1046294528 bytes (1.0 GB) copied, 122.165 s, 8.6 MB/s

```

I got the same thing for the second option too
```
gunzip ubuntu-11.04-preinstalled-netbook-armel+omap.img
sudo dd bs=4M if=uubuntu-11.04-preinstalled-netbook-armel+omap.img of=/dev/mmcblk
sync 
```

and this is the error I get from the 2nd option

```
dd: writing `/dev/mmcblk': No space left on device
250+0 records in
249+0 records out
1046294528 bytes (1.0 GB) copied, 27.7209 s, 37.7 MB/s

```

any Ideas?



here is my fdisk

```
Disk /dev/mmcblk0: 3965 MB, 3965190144 bytes
4 heads, 16 sectors/track, 121008 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ab1ab

```

---

### Post by bneva on 2011-09-06
bump

---

