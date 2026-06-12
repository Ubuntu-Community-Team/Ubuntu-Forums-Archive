---
title: "ipod video won't mount"
date: 2010-05-17
forum: General Help
---

### Post by log1c on 2010-05-17
so. i've been using lucid for a few weeks so far, and i'm loving it so far. i do have one issue, though. i was mixing some music with audacity earlier, and i connected my ipod to pull a few songs off of it. it took a little while for it to mount, but i eventually got it mounted and opened with rhythmbox. after i finished my mix, i went to put it onto my ipod via rhythmbox, but it refused to copy. i unplugged my ipod and plugged it back in, but nothing happened. i left it sitting for nearly an hour, and still nothing. i ran lsusb in a shell and it tells me that my ipod is connected. furthermore, i went to /tmp/ipodqoSdTy and all of my ipod's files are showing up (i recognize them from my many adventures in recovering my music after a crash). i decided to download gtkpod and see if i could mount it with that, and after i choose my ipod type, the program suddenly quit. i tried this about 3 more times, and got the same result. i've tried using gconf-editor to adjust my nautilus automount preferences, and still nothing. i've been researching the problem, and it seems that several other people are having this problem as well. i have to say that i'm disappointed with 10.04. i may have to revert back to using 9.10 if i can't get this problem solved. anyone know a solution?

tl;dr, ipod won't mount in 10.04

---

### Post by blazemore on 2010-05-18
Please post the output from running the command
```
sudo fdisk -l
```

Essentially, this command lists all mountable partitions attached to your system

---

### Post by log1c on 2010-05-18
here's the output 
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb8189460

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12163    97695744   83  Linux
/dev/sda2           12163       13379     9764865    5  Extended
/dev/sda5           12163       13379     9764864   82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
84 heads, 62 sectors/track, 7502 cylinders
Units = cylinders of 5208 * 2048 = 10665984 bytes
Sector size (logical/physical): 2048 bytes / 2048 bytes
I/O size (minimum/optimal): 2048 bytes / 2048 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          13      128394    0  Empty
Partition 1 does not end on cylinder boundary.
Partition 1 does not start on physical sector boundary.
/dev/sdb2              13        7503    78022222    b  W95 FAT32

```

it's definitely connected, i just don't know why nautilus won't see it


also: i've tried manually dumping files into the music folder in ipod_control. the folder seems to be locked, as does the rest of the folders and files. i've added music to my ipod this way before on previous distros, so i don't have any idea what's going on here

also: i just tried connecting it to my sister's laptop running linux mint 8. it pops up on the desktop, i can browse through all of the files and folders, but when i try and open it with rythmbox, rythmbox crashes and refuses to open. i tried opening it with banshee. banshee opens fine, but won't recognize that my ipod is connected....

anyways, i'll also include the output from lsusb just incase
```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05ac:1209 Apple, Inc. iPod Video
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

as well as a screenshot from running nautilus as root and running nautilus as an administrator:

---

### Post by log1c on 2010-05-20
i'm going to have to switch back to karmic today unless i find a solution. i'm disappointed with 10.04

---

