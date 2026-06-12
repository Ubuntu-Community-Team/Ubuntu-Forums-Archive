---
title: "usb mp3 player &quot;Filesystem error&quot;"
date: 2011-11-01
forum: General Help
---

### Post by rudecam on 2011-11-01
the usb mp3 player is been detected, i even get a file browser window that pops up but it remains blank.
on a windows vista, it shows no sign of problem.
the mp3 player plays it's track just like normal.
```
dmesg
[   38.460202] wlan0: no IPv6 routers present
[   44.056224] usb 2-3: new high speed USB device using ehci_hcd and address 3
[   44.190919] usb 2-3: configuration #1 chosen from 1 choice
[   44.191448] scsi7 : SCSI emulation for USB Mass Storage devices
[   44.191594] usb-storage: device found at 3
[   44.191596] usb-storage: waiting for device to settle before scanning
[   49.188502] usb-storage: device scan complete
[   49.189087] scsi 7:0:0:0: Direct-Access              COBY MP3 Player       PQ: 0 ANSI: 0 CCS
[   49.189803] sd 7:0:0:0: Attached scsi generic sg3 type 0
[   49.192423] sd 7:0:0:0: [sdc] 7948288 512-byte logical blocks: (4.06 GB/3.79 GiB)
[   49.192913] sd 7:0:0:0: [sdc] Write Protect is off
[   49.192918] sd 7:0:0:0: [sdc] Mode Sense: 3b 00 00 00
[   49.192922] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[   49.195037] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[   49.195044]  sdc: sdc1
[   49.197651] sd 7:0:0:0: [sdc] Assuming drive cache: write through
[   49.197656] sd 7:0:0:0: [sdc] Attached SCSI removable disk
[   49.609155] FAT: Filesystem error (dev sdc1)
[   49.609159]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.609162]     File system has been set read-only
[   49.609263] FAT: Filesystem error (dev sdc1)
[   49.609265]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.609352] FAT: Filesystem error (dev sdc1)
[   49.609354]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.609435] FAT: Filesystem error (dev sdc1)
[   49.609437]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.609521] FAT: Filesystem error (dev sdc1)
[   49.609523]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.609604] FAT: Filesystem error (dev sdc1)
[   49.609606]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.609687] FAT: Filesystem error (dev sdc1)
[   49.609689]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.609770] FAT: Filesystem error (dev sdc1)
[   49.609772]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.609853] FAT: Filesystem error (dev sdc1)
[   49.609855]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.609929] FAT: Filesystem error (dev sdc1)
[   49.609931]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.610004] FAT: Filesystem error (dev sdc1)
[   49.610006]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.610075] FAT: Filesystem error (dev sdc1)
[   49.610077]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.610146] FAT: Filesystem error (dev sdc1)
[   49.610147]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.610216] FAT: Filesystem error (dev sdc1)
[   49.610218]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.610287] FAT: Filesystem error (dev sdc1)
[   49.610289]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.610361] FAT: Filesystem error (dev sdc1)
[   49.610363]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.610444] FAT: Filesystem error (dev sdc1)
[   49.610445]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.610527] FAT: Filesystem error (dev sdc1)
[   49.610529]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.616430] FAT: Filesystem error (dev sdc1)
[   49.616434]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.616528] FAT: Filesystem error (dev sdc1)
[   49.616530]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.616613] FAT: Filesystem error (dev sdc1)
[   49.616615]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.616696] FAT: Filesystem error (dev sdc1)
[   49.616698]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.616786] FAT: Filesystem error (dev sdc1)
[   49.616788]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.616871] FAT: Filesystem error (dev sdc1)
[   49.616873]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.616954] FAT: Filesystem error (dev sdc1)
[   49.616956]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.617037] FAT: Filesystem error (dev sdc1)
[   49.617039]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.617121] FAT: Filesystem error (dev sdc1)
[   49.617123]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.617198] FAT: Filesystem error (dev sdc1)
[   49.617200]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.617274] FAT: Filesystem error (dev sdc1)
[   49.617276]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.617345] FAT: Filesystem error (dev sdc1)
[   49.617347]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.617416] FAT: Filesystem error (dev sdc1)
[   49.617418]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.617487] FAT: Filesystem error (dev sdc1)
[   49.617489]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.617558] FAT: Filesystem error (dev sdc1)
[   49.617560]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.617632] FAT: Filesystem error (dev sdc1)
[   49.617634]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.617714] FAT: Filesystem error (dev sdc1)
[   49.617716]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.617799] FAT: Filesystem error (dev sdc1)
[   49.617801]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.630978] FAT: Filesystem error (dev sdc1)
[   49.630982]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   49.631043] FAT: Filesystem error (dev sdc1)
[   49.631046]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   50.589274] FAT: Filesystem error (dev sdc1)
[   50.589278]     fat_get_cluster: invalid cluster chain (i_pos 0)
[   50.832993] FAT: Filesystem error (dev sdc1)
[   50.832996]     fat_get_cluster: invalid cluster chain (i_pos 0)

```
```

rudecam@***:~$ sudo fdisk -l
[sudo] password for rudecam: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcf5acf27

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1918    15360000    7  HPFS/NTFS
/dev/sda3            1919       21040   153597465    7  HPFS/NTFS
/dev/sda4           21041       60801   319380202    5  Extended
/dev/sda5           21041       22315    10241406   82  Linux swap / Solaris
/dev/sda6           22316       60801   309138763+  83  Linux

[COLOR="Red"]Disk /dev/sdc[/COLOR]: 4069 MB, 4069523456 bytes
8 heads, 32 sectors/track, 31048 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x221e5780

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       31048     3974128    b  W95 FAT32
rudecam@***:~$ sudo sfdisk -d /dev/sda > Desktop/PTsda.txt
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
```
```
rudecam@***:/media/9CED-5751$ ls -als
[COLOR="Red"]ls: cannot access .Trash-1000: Input/output error[/COLOR]
total 2208
   8 drwx------  9 rudecam rudecam    8192 1969-12-31 19:00 .
   4 drwxr-xr-x  3 root    root       4096 2011-11-01 15:55 ..
   4 drwx------ 12 rudecam rudecam    4096 2011-02-08 04:28 Digital Fortress
 624 -rwxr-xr-x  1 rudecam rudecam  635904 2009-12-03 11:13 exemple pour travail long.doc
   4 drwx------  8 rudecam rudecam    4096 2011-10-31 09:14 géomatique
  12 drwx------  2 rudecam rudecam   12288 2011-10-25 11:42 LES PARTICULES ÉLÉMENTAIRES_ houellebecq
   4 drwx------  4 rudecam rudecam    4096 2011-09-11 19:19 MARIE MADELAINE LE LIVRE DE L'ELUE_kathleen mcgowan
1536 -rwxr-xr-x  1 rudecam rudecam 1570275 2011-10-26 10:00 Projections_Carto_2009.pdf
   4 drwx------  4 rudecam rudecam    4096 2011-10-05 00:31 run osti
   4 drwx------  3 rudecam rudecam    4096 2010-12-07 17:44 .Spotlight-V100
   [COLOR="Red"]? d?????????  ? ?       ?             ?                ? .Trash-1000[/COLOR]
   4 -rwxr-xr-x  1 rudecam rudecam    4096 2010-12-07 17:44 ._.Trashes

```

i don't want to lose the firmware so i'm shy at using the shred command.

---

### Post by rudecam on 2011-11-04
*bump*

sorry about that, ideas anyone?

---

### Post by rudecam on 2011-11-05
made a format of the drive. since all of the corrupted files were gone. I was scared the firmware necessary to operate the mp3 player would be erased too but it didn't. I used a simple windows format but i think system>administration>disk utility offers the same sort of things.

---

