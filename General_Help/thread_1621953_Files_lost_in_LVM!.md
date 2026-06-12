---
title: "Files lost in LVM!?"
date: 2010-11-14
forum: General Help
---

### Post by kloneme on 2010-11-14
So I was messing around with LVM trying to turn 3 ~300GB drives into one LVM under 1TB. I scrapped the idea after not being able to combine hdc and hdd into a VG called doctor/frankenstein while using hde as swap space to move the single ext3 primaries onto the VG. I am now battling to recover the contents of hdc back! 

```

frankie:/dark# pvscan
  PV /dev/hde1   VG monster   lvm2 [279.47 GB / 9.47 GB free]
  PV /dev/hdc1   VG doctor    lvm2 [298.09 GB / 18.09 GB free]
  Total: 2 [577.56 GB] / in use: 2 [577.56 GB] / in no VG: 0 [0   ]
frankie:/dark# fdisk -l

Disk /dev/hde: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdb94e58a

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1       36483   293049666   8e  Linux LVM

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x230f230f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         851     6835626   83  Linux
/dev/hda2             852        9964    73200172+   5  Extended
/dev/hda5             852        1122     2176776   82  Linux swap / Solaris
/dev/hda6            1123        9964    71023333+  83  Linux

Disk /dev/hdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d12b4d6

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       38913   312568641   8e  Linux LVM

Disk /dev/hdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/hdd doesn't contain a valid partition table

Disk /dev/dm-0: 289.9 GB, 289910292480 bytes
255 heads, 63 sectors/track, 35246 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 300.6 GB, 300647710720 bytes
255 heads, 63 sectors/track, 36551 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table
frankie:/dark# lvdisplay
  --- Logical volume ---
  LV Name                /dev/monster/darkness
  VG Name                monster
  LV UUID                0alOcL-UudD-Amqd-MIjL-caRE-ULUY-zSlZRH
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                270.00 GB
  Current LE             69120
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:0

  --- Logical volume ---
  LV Name                /dev/doctor/frankenstein
  VG Name                doctor
  LV UUID                jTdVR2-yCto-GYh5-f3d7-iQtZ-FHeV-NtSqHc
  LV Write Access        read/write
  LV Status              available
  # open                 1
  LV Size                280.00 GB
  Current LE             71680
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           254:1

frankie:/dark# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             6.5G  981M  5.2G  16% /
tmpfs                 364M     0  364M   0% /lib/init/rw
udev                   10M  680K  9.4M   7% /dev
tmpfs                 364M     0  364M   0% /dev/shm
/dev/hda6              67G  1.2G   63G   2% /home
deathstar.satan:/chasm
                      917G  780G   92G  90% /chasm
/dev/mapper/monster-darkness
                      266G   30G  224G  12% /lvmtest
/dev/hdd              294G  172G  107G  62% /light
/dev/mapper/doctor-frankenstein
                      276G  192M  262G   1% /dark

```

This is my first post ever, things I have followed(or in the process) with no luck are:
[http://www.penguinlinux.com/blog/general-linux/recovering-a-crashed-lvm2-pv-hard-drive/](http://www.penguinlinux.com/blog/general-linux/recovering-a-crashed-lvm2-pv-hard-drive/)

[http://grover.open2space.com/node/17](http://grover.open2space.com/node/17)

---

### Post by kloneme on 2010-11-21
So I have pretty much given up on trying to use the UUID method or anything to do with LVM, I'm pretty sure the headers were messed up in a mkfs.ext3 after I panicked. Luckily(semi) I have dd_rhelp'd the LVM disk and have an image of it now. I have tried many recovery methods with foremost, scalpel, and now testdisk/photorec. PhotoRec being the best so far I hope to recover the *.iso files as best a possible, but the snag is it looks through the cd image and just pulls the files from it rather than the whole ISO. I have learned tons so far, just wish it wasn't with data I actually wanted to keep. 

```
frankie:/light# ls -lah
total 269G
drwxr-xr-x  4 root     root     4.0K 2000-12-31 18:46 .
drwxr-xr-x 30 root     root     4.0K 2010-11-21 13:19 ..
drwxr-xr-x  3 www-data www-data 4.0K 2009-04-21 16:49 dd_rhelp-0.1.2
drwx------  2 root     root      16K 2010-11-19 21:17 lost+found
-rw-r--r--  1 root     root     268G 2001-01-01 08:19 nomore.img
-rw-r--r--  1 root     root     2.7K 2001-01-01 08:19 nomore.img.log

```


Biggest thing I learned is data is far but deleted from this HDD and I'm finding lots of transitional data from just data moves in the past. 

Any comments or suggestions would still be appreciated.

---

