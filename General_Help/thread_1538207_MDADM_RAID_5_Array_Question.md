---
title: "MDADM RAID 5 Array Question"
date: 2010-07-24
forum: General Help
---

### Post by jmg999 on 2010-07-24
Hi,

I have a fileserver w/ Promise EX 8350 controller card in it.  Attached are 8x500GB HDDs.  I currently have them setup as JBOD, so I can see the drives w/ fdisk.

```


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
15 heads, 1 sectors/track, 65118211 cylinders
Units = cylinders of 15 * 512 = 7680 bytes
Disk identifier: 0x00000000

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            8990    25192541   188876635+  b7  BSDI fs
/dev/sdb2   *           1           1           0    0  Empty
Partition 2 does not end on cylinder boundary.
/dev/sdb3       143174566   162888046   147851099+  b7  BSDI fs
/dev/sdb4   ?           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      267350  2147483647+  ee  EFI GPT

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
11 heads, 1 sectors/track, 88797560 cylinders
Units = cylinders of 11 * 512 = 5632 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1           12166       12415        1371+  b7  BSDI fs
/dev/sdd2   *           1           1           0    0  Empty
Partition 2 does not end on cylinder boundary.
/dev/sdd3       195237952   195238201        1371+  b7  BSDI fs
/dev/sdd4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sde: 500.1 GB, 500107862016 bytes
7 heads, 1 sectors/track, 139539024 cylinders
Units = cylinders of 7 * 512 = 3584 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1           18971       19216         859+  b7  BSDI fs
/dev/sde2   *           1           1           0    0  Empty
Partition 2 does not end on cylinder boundary.
/dev/sde3       306802349   306802594         859+  b7  BSDI fs
/dev/sde4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2d4d690

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   ?      239465      367703  1030072844+  da  Non-FS data
Partition 1 does not end on cylinder boundary.
/dev/sdf2   ?       39805       67636   223555650   2f  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdf3   ?       98145      304904  1660787832+  e8  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdf4   ?      109338      353855  1964082099   55  EZ-Drive
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
23 heads, 1 sectors/track, 42468398 cylinders
Units = cylinders of 23 * 512 = 11776 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1            5952        6205        2907+  b7  BSDI fs
/dev/sdg2   *           1           1           0    0  Empty
Partition 2 does not end on cylinder boundary.
/dev/sdg3        93374806    93375059        2907+  b7  BSDI fs
/dev/sdg4   *           1           1           0    0  Empty
Partition 4 does not end on cylinder boundary.

Disk /dev/sdh: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2d4d690

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   ?      239473      393711  1238915752+  83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sdh2   ?       39805       67636   223555650   2f  Unknown
Partition 2 does not end on cylinder boundary.
/dev/sdh3   ?      231812      453582  1781371683   5f  Unknown
Partition 3 does not end on cylinder boundary.
/dev/sdh4   *      109338      353855  1964082099   55  EZ-Drive
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5745e6e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdj: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8844ad1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdk: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05563535

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdl: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6603c74

   Device Boot      Start         End      Blocks   Id  System
/dev/sdl1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdm: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff2ebb89

   Device Boot      Start         End      Blocks   Id  System
/dev/sdm1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdn: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5be14e4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdn1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdo: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe4fb07e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdo1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdp: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7135fa61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdp1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/md0: 7001.4 GB, 7001415221248 bytes
2 heads, 4 sectors/track, 1709329888 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/sdq: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b4bef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdq1               1         365     2931831   82  Linux swap / Solaris
/dev/sdq2             366       30401   241264170   83  Linux 
```

I have another array set as /dev/md0.  /dev/sdg is the OS HDD.  I want to create a RAID 5 array w/ the drives attached to the Promise card, but I'd like to use mdadm, and use the card only as a controller card.  From what I've read here: [http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461) I just want to see if I understand correctly.  If I run the following commands, will I be able to create a RAID 5 array?

```
mdadm --create /dev/md1 --chunk=64 --level=raid5 --raid devices=8 /dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde /dev/sdf /dev/sdg /dev/sdh

mdadm --assemble /dev/md1 /dev/sda /dev/sdb /dev/sdc /dev/sdd /dev/sde /dev/sdf /dev/sdg /dev/sdh

mkfs.ext3 /dev/md1 
```

Any help would be greatly appreciated.  Thank you.

---

### Post by rubylaser on 2010-07-24
You'll want to fdisk each of those drives, and delete all existing partitions with fdisk (obviously backup any data on them first).  Then I use fdisk create a new partition id, and set it and linux raid like this...
```
server1:~# fdisk /dev/sdb

The number of cylinders for this disk is set to 10443.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
(e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): [COLOR="Red"]<-- m[/COLOR]
Command action
  a   toggle a bootable flag
  b   edit bsd disklabel
  c   toggle the dos compatibility flag
  d   delete a partition
  l   list known partition types
  m   print this menu
  n   add a new partition
  o   create a new empty DOS partition table
  p   print the partition table
  q   quit without saving changes
  s   create a new empty Sun disklabel
  t   change a partition's system id
  u   change display/entry units
  v   verify the partition table
  w   write table to disk and exit
  x   extra functionality (experts only)

Command (m for help): [COLOR="red"]<-- n[/COLOR]
Command action
  e   extended
  p   primary partition (1-4)
[COLOR="red"]<-- p[/COLOR]
Partition number (1-4): [COLOR="red"]<-- 1[/COLOR]
First cylinder (1-10443, default 1): [COLOR="red"]<-- <ENTER>[/COLOR]
Using default value 1
Last cylinder or +size or +sizeM or +sizeK (1-10443, default 10443): [COLOR="red"]<-- <ENTER>[/COLOR]
 
Command (m for help): [COLOR="red"]<-- t[/COLOR]
Selected partition 1
Hex code (type L to list codes): [COLOR="red"]<-- L[/COLOR]

0  Empty           1e  Hidden W95 FAT1 80  Old Minix       be  Solaris boot
1  FAT12           24  NEC DOS         81  Minix / old Lin bf  Solaris
2  XENIX root      39  Plan 9          82  Linux swap / So c1  DRDOS/sec (FAT-
3  XENIX usr       3c  PartitionMagic  83  Linux           c4  DRDOS/sec (FAT-
4  FAT16 <32M      40  Venix 80286     84  OS/2 hidden C:  c6  DRDOS/sec (FAT-
5  Extended        41  PPC PReP Boot   85  Linux extended  c7  Syrinx
6  FAT16           42  SFS             86  NTFS volume set da  Non-FS data
7  HPFS/NTFS       4d  QNX4.x          87  NTFS volume set db  CP/M / CTOS / .
8  AIX             4e  QNX4.x 2nd part 88  Linux plaintext de  Dell Utility
9  AIX bootable    4f  QNX4.x 3rd part 8e  Linux LVM       df  BootIt
a  OS/2 Boot Manag 50  OnTrack DM      93  Amoeba          e1  DOS access
b  W95 FAT32       51  OnTrack DM6 Aux 94  Amoeba BBT      e3  DOS R/O
c  W95 FAT32 (LBA) 52  CP/M            9f  BSD/OS          e4  SpeedStor
e  W95 FAT16 (LBA) 53  OnTrack DM6 Aux a0  IBM Thinkpad hi eb  BeOS fs
f  W95 Ext'd (LBA) 54  OnTrackDM6      a5  FreeBSD         ee  EFI GPT
10  OPUS            55  EZ-Drive        a6  OpenBSD         ef  EFI (FAT-12/16/
11  Hidden FAT12    56  Golden Bow      a7  NeXTSTEP        f0  Linux/PA-RISC b
12  Compaq diagnost 5c  Priam Edisk     a8  Darwin UFS      f1  SpeedStor
14  Hidden FAT16 <3 61  SpeedStor       a9  NetBSD          f4  SpeedStor
16  Hidden FAT16    63  GNU HURD or Sys ab  Darwin boot     f2  DOS secondary
17  Hidden HPFS/NTF 64  Novell Netware  b7  BSDI fs         fd  Linux raid auto
18  AST SmartSleep  65  Novell Netware  b8  BSDI swap       fe  LANstep
1b  Hidden W95 FAT3 70  DiskSecure Mult bb  Boot Wizard hid ff  BBT
1c  Hidden W95 FAT3 75  PC/IX
Hex code (type L to list codes): [COLOR="red"]<-- fd[/COLOR]
Changed system type of partition 1 to fd (Linux LVM)

Command (m for help): [COLOR="red"]<-- w[/COLOR]
The partition table has been altered!
 
Calling ioctl() to re-read partition table.
Syncing disks.
```

After fdisking each of them, they should look like this...
```
raidtest:~# fdisk -l

Disk /dev/sda: 5368 MB, 5368709120 bytes
255 heads, 63 sectors/track, 652 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          12       96358+  83  Linux
/dev/sda2              13         652     5140800    5  Extended
/dev/sda5              13         134      979933+  82  Linux swap / Solaris
/dev/sda6             135         652     4160803+  83  Linux

Disk /dev/sdb: 21.4 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
 
  Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2610    20964793+  fd  Linux raid autodetect
 
Disk /dev/sdc: 21.4 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        2610    20964793+  fd  Linux raid autodetect

Disk /dev/sdd: 21.4 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        2610    20964793+  fd  Linux raid autodetect
 
Disk /dev/sde: 21.4 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        2610    20964793+  fd  Linux raid autodetect
 
Disk /dev/sdf: 21.4 GB, 21474836480 bytes
255 heads, 63 sectors/track, 2610 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

  Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1        2610    20964793+  fd  Linux raid autodetect
```

Then, you could use your mdadm create line...

```
mdadm --create /dev/md1 --chunk=64 --level=raid5 --raid devices=8 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1
```

mdadm will automatically assemble the array for you and begin syncing the disks.  I usually do this to watch it build...
```
watch cat /proc/mdstat
```

When it's done syncing, you can add the filesystem, either ext3 or ext4

```
mkfs.ext3 /dev/md1

```
```
mkfs.ext4 /dev/md1

```

Hope that helps.

---

### Post by jmg999 on 2010-07-24
rubylaser, thank you so much for the in-depth reply.  I will give this a shot, and report back.  Thanks, again!

---

### Post by jmg999 on 2010-07-24
So, I ran the commands as you suggested, and as it turned out, I had to delete the previous partitions first.  So, I did that, and one of the drives contained a GUID Partition Table, so I used DD to overwrite it, then partitioned it.  The partitioning came out fine, and I ran this command:

>  sudo mdadm --create /dev/md1 --chunk=64 --level=raid5 --raid-devices=8 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1 
mdadm: array /dev/md1 started. 

So, then ran the watch cat /proc/mdstat.  It seemed to start off normally, but then the speeds began do drop precipitously.  It got all the way down to 120K/s, and then it began to spike back up again, before it just completely stopped about two minutes into the routine.  I then ran a cat /proc/mdstat:

> cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md1 : active raid5 sdh1[8](S) sdg1[6] sdf1[5] sde1[4] sdd1[3] sdc1[2] sdb1[9](F) sda1[0]
      3418687552 blocks level 5, 64k chunk, algorithm 2 [8/6] [U_UUUUU_]
      
md0 : active raid5 sdi1[0] sdp1[7] sdo1[6] sdn1[5] sdm1[4] sdl1[3] sdk1[2] sdj1[1]
      6837319552 blocks level 5, 64k chunk, algorithm 2 [8/8] [UUUUUUUU]
      
unused devices: <none> 

As you can see, it's missing two drives, and it shows multiple RAID levels in its personalities, which is something that I'd not seen before.  So, I ran an fdisk -l...

> sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa5407036

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2d4d690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdg: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdh: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf2d4d690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       60801   488384001   fd  Linux raid autodetect

Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5745e6e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdj: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8844ad1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdk: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05563535

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdl: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc6603c74

   Device Boot      Start         End      Blocks   Id  System
/dev/sdl1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdm: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xff2ebb89

   Device Boot      Start         End      Blocks   Id  System
/dev/sdm1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdn: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5be14e4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdn1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdo: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbe4fb07e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdo1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdp: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7135fa61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdp1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/md0: 7001.4 GB, 7001415221248 bytes
2 heads, 4 sectors/track, 1709329888 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/sdq: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b4bef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdq1               1         365     2931831   82  Linux swap / Solaris
/dev/sdq2             366       30401   241264170   83  Linux

Disk /dev/md1: 3500.7 GB, 3500736053248 bytes
2 heads, 4 sectors/track, 854671888 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md1 doesn't contain a valid partition table 

Everything looks good there, so ran the --created command again...

> sudo mdadm --create /dev/md1 --chunk=64 --level=raid5 --raid-devices=8 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1
mdadm: another array by this name is already running. 

Any thoughts?

---

### Post by rubylaser on 2010-07-24
It won't let you make a mdadm device with the same name.  You already have a /dev/md1, so you can't make another one without destroying that one first.

Here's what mine looks like at home (I have a hot spare and 9 500GB drives)
```
fileserver ~: mdadm --detail --scan /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Fri Mar 28 16:10:12 2008
     Raid Level : raid5
     Array Size : 3418687552 (3260.31 GiB 3500.74 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 8
  Total Devices : 9
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sat Jul 24 20:09:45 2010
          State : clean
 Active Devices : 8
Working Devices : 9
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : c2e82ef8:7bb882b4:c0279fe2:a22aea10
         Events : 0.1317716

    Number   Major   Minor   RaidDevice State
       0       8       81        0      active sync   /dev/sdf1
       1       8       65        1      active sync   /dev/sde1
       2       8       17        2      active sync   /dev/sdb1
       3       8       49        3      active sync   /dev/sdd1
       4       8      113        4      active sync   /dev/sdh1
       5       8      144        5      active sync   /dev/sdj
       6       8       96        6      active sync   /dev/sdg
       7       8      128        7      active sync   /dev/sdi

       8       8       33        -      spare   /dev/sdc1
```

Can you run this command and see what disks it's missing?
```
mdadm --detail --scan /dev/md0

```

mdadm is reporting /dev/sdh1 added as a spare, and /dev/sda1 as failed.  You'll probably want to run smartmontools over /dev/sda, but you can add /dev/sdh1 to the array like this...
```
mdadm –add /dev/md1 /dev/sdh1
```

Let me know what you get..

---

### Post by rubylaser on 2010-07-24
To use smartmontools
```
sudo apt-get install smartmontools
```

And to test the disk

```
smartctl -d ata -H /dev/sda
```

If it comes back healthy you can remove it from the array, and then add it back like this...
```
mdadm --manage /dev/md1 --remove /dev/sda1
```
```
mdadm --manage /dev/md1 --add /dev/sda1
```

---

### Post by jmg999 on 2010-07-24
Thanks for the quick reply.  I'll test it out right now and let you know.

---

### Post by jmg999 on 2010-07-24
> sudo mdadm --detail --scan /dev/md1 
/dev/md1:
        Version : 00.90.03
  Creation Time : Sat Jul 24 16:38:00 2010
     Raid Level : raid5
     Array Size : 3418687552 (3260.31 GiB 3500.74 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sat Jul 24 16:40:02 2010
          State : clean, degraded
 Active Devices : 6
Working Devices : 7
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 27bc4780:96f4ee9d:72560c0a:77e3a89a (local to host USC)
         Events : 0.6

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        1      removed
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
       4       8       65        4      active sync   /dev/sde1
       5       8       81        5      active sync   /dev/sdf1
       6       8       97        6      active sync   /dev/sdg1
       7       0        0        7      removed

       8       8      113        -      spare   /dev/sdh1
       9       8       17        -      faulty spare   /dev/sdb1

I'll try the other commands now.

---

### Post by jmg999 on 2010-07-24
This is what I tried...

> sudo mdadm --add /dev/md1 /dev/sdh1
mdadm: Cannot open /dev/sdh1: Device or resource busy

> sudo smartctl -d ata /dev/sdh
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Smartctl: Device Read Identity Failed (not an ATA/ATAPI device)

A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.

---

### Post by jmg999 on 2010-07-24
Also, I thought I'd try this just in case...

> sudo mdadm --stop /dev/md1 
mdadm: stopped /dev/md1
sudo mdadm --add /dev/md1 /dev/sdh1 
mdadm: cannot get array info for /dev/md1

---

### Post by jmg999 on 2010-07-24
I was looking over the man page for smartctl, and it seems the syntax is a bit different, if the HDD is behind a controller card.

> sudo smartctl -H /dev/sdb
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

SMART Health Status: OK

---

### Post by rubylaser on 2010-07-24
Did the original drive that was showing failed as failed when you added it to the array (originally /dev/sda) pass the SMART test?  This is hard for me to keep track of the disks, because I'm not physically in front of the server.

You can't add a disk to a stopped array, so that's why trying to add sdh to md1 failed when it was stopped.

If you don't have any data on those drives yet, it might make sense to blow /dev/md1 away, and  start over.  Here's how you would do that.  **Only do this if the array doesn't contain data, or if you've backed it up.**

```
mdadm --stop /dev/md1
mdadm --remove /dev/md1
```

and finally we can even delete the superblock from the individual drives:
```
mdadm --zero-superblock /dev/sda
mdadm --zero-superblock /dev/sdb
mdadm --zero-superblock /dev/sdc
mdadm --zero-superblock /dev/sdd
mdadm --zero-superblock /dev/sde
mdadm --zero-superblock /dev/sdf
mdadm --zero-superblock /dev/sdg
mdadm --zero-superblock /dev/sdh
```

Then, try to reassemble the array.

```
sudo mdadm --create --verbose /dev/md1 --level=5 --raid-devices=8 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1
```

Or the compact way...

```
sudo mdadm -Cv /dev/md1 -l5 -n8 /dev/sd[abcdefgh]1
```

---

### Post by jmg999 on 2010-07-24
I'm thinking that it has something to do w/ the way the array is setup by the Promise controller.  There's no option in either the BIOS or the webpam app to tell it to not use RAID.  The closest I could get was to set it to use JBOD.

---

### Post by jmg999 on 2010-07-24
Well, it doesn't really test it.  It just automatically pops up a status that says it's OK.

---

### Post by jmg999 on 2010-07-24
The array was already stopped at this point.

> sudo mdadm --remove /dev/md1 
sudo mdadm --zero-superblock /dev/sda
mdadm: Unrecognised md component device - /dev/sda
sudo mdadm --zero-superblock /dev/sda1
sudo mdadm --zero-superblock /dev/sdb1
sudo mdadm --zero-superblock /dev/sdc1
sudo mdadm --zero-superblock /dev/sdd1
sudo mdadm --zero-superblock /dev/sde1
sudo mdadm --zero-superblock /dev/sdf1
sudo mdadm --zero-superblock /dev/sdg1
sudo mdadm --zero-superblock /dev/sdh1

I ran the mdadm --create command again, and it did the same thing.  It runs all right for about 30 seconds, and all of a sudden, the speed drops very quickly down to nothing, until it stops after about 60 seconds.  It then reports the same info as before...

> jeffe@USC:~$ mdadm --detail /dev/md1
mdadm: cannot open /dev/md1: Permission denied
jeffe@USC:~$ sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 00.90.03
  Creation Time : Sat Jul 24 19:20:16 2010
     Raid Level : raid5
     Array Size : 3418687552 (3260.31 GiB 3500.74 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sat Jul 24 19:22:13 2010
          State : clean, degraded
 Active Devices : 6
Working Devices : 7
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : e80b0dc8:4db95f2d:72560c0a:77e3a89a (local to host USC)
         Events : 0.6

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       0        0        1      removed
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1
       4       8       65        4      active sync   /dev/sde1
       5       8       81        5      active sync   /dev/sdf1
       6       8       97        6      active sync   /dev/sdg1
       7       0        0        7      removed

       8       8      113        -      spare   /dev/sdh1
       9       8       17        -      faulty spare   /dev/sdb1

---

### Post by rubylaser on 2010-07-24
I'm at a loss.  I've set arrays like this up at work on many machines, and ran 4 arrays at home over the years. Currently at home and work I use either Supermicro's AOC-Saslp-MV8 and their PCI-X AOC-SAT2-MV8 cards and they work great for me.  These are both controllers with no onboard raid functionality.  I've flashed other softraid cards and used mdadm with them, as well as using mdadm with instead of the hardware controllers.

---

### Post by rubylaser on 2010-07-24
One other thing you could try, is to clear the array again, and start with 3 disks, and add new ones in like this.

```
mdadm --create --verbose /dev/md1 --level=5 --raid-devices=3 /dev/sda1 /dev/sdb1 /dev/sdc1
```
```
mkfs.ext3 /dev/md1
```
Then, add another disk
```
mdadm --add /dev/md1 /dev/sdd1
```
And, grow the array to the new disk
```
mdadm --grow /dev/md1 --raid-devices=4
```
```
mdadm --add /dev/md1 /dev/sde1
```
```
mdadm --grow /dev/md1 --raid-devices=5
```
See if this will work.  If so, keep adding disks in the same fashion
```
mdadm --add /dev/md1 /dev/sdf1
```
```
mdadm --grow /dev/md1 --raid-devices=6
```
```
mdadm --add /dev/md1 /dev/sdg1
```
```
mdadm --grow /dev/md1 --raid-devices=7
```
```
mdadm --add /dev/md1 /dev/sdh1
```
```
mdadm --grow /dev/md1 --raid-devices=8
```
Finally, grow your filesystem to the new space...
```
fsck.ext3 /dev/md1
```
```
resize2fs /dev/md1
```

I doubt it will work, but it's worth a shot.

---

### Post by jmg999 on 2010-07-25
I tried out your most recent suggestion, and it didn't work, either.  First, I tried creating the array w/ /dev/sda1, /dev/sdb1, and /dev/sdc1.  That suffered the same fate as my previous attempts.  There seemed to be a question about the validity of /dev/sdb1, so I decided to try again w/ /dev/sda1, /dev/sdc1, and /dev/sdd1.  That seemed to work better, as it ran for about 20-30 minutes, but it eventually crapped out.  This was the read-out from this most recent attempt...

> jeffe@USC:~$ sudo mdadm --detail /dev/md1 
[sudo] password for jeffe: 
/dev/md1:
        Version : 00.90.03
  Creation Time : Sun Jul 25 00:09:43 2010
     Raid Level : raid5
     Array Size : 976767872 (931.52 GiB 1000.21 GB)
  Used Dev Size : 488383936 (465.76 GiB 500.11 GB)
   Raid Devices : 3
  Total Devices : 3
Preferred Minor : 1
    Persistence : Superblock is persistent

    Update Time : Sun Jul 25 00:22:26 2010
          State : clean, degraded
 Active Devices : 1
Working Devices : 2
 Failed Devices : 1
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 960afb9b:8afca97f:72560c0a:77e3a89a (local to host USC)
         Events : 0.6

    Number   Major   Minor   RaidDevice State
       0       0        0        0      removed
       1       8       33        1      active sync   /dev/sdc1
       2       0        0        2      removed

       3       8       49        -      spare   /dev/sdd1
       4       8        1        -      faulty spare   /dev/sda1

At this point, I'm guessing that there's nothing wrong w/ any of these HDDs, and the problem, instead, appears to be something unrelated.  I still think it has to do w/ the way the drives are setup by Promise.  I tried searching online about using this card w/ no RAID capabilities, but I couldn't find anything.

---

### Post by jmg999 on 2010-07-25
I found this thread in the archives...

[http://ubuntuforums.org/archive/index.php/t-976328.html](http://ubuntuforums.org/archive/index.php/t-976328.html)

It doesn't address my controller card, in particular, but it does all of the cards mentioned were Promise cards.  So, I've decided to upgrade to 10.04 LTS.  I'm in process now, and I'll try to build the array again, once it's finished.  I'll post back, when I'm done.

---

### Post by jmg999 on 2010-07-25
Well, the upgrade went off w/out a hitch, but no go on the array.  The same problem occurred.  I might try building the array utilizing the the Promise card's RAID capabilities just to see if it works.

---

### Post by rubylaser on 2010-07-25
The Promise card that's mentioned in that post should work fine with modern kernels, it's just a 4 port controller.  Unraid (uses a linux kernel), actually uses those cards in the machines they build.  I'm sure you're spot on about the way that your Promise card is presenting the drives to Linux causing a problem.

Please post back the results of building an array using the card's RAID.  At this point, I just want to make sure that you get some form of functioning RAID.

---

### Post by jmg999 on 2010-07-25
The card I'm using is an 8-port controller.  It's the SuperTrak EX 8350.  It's actually a replacement.  The first one I had died on me after ~two years.  That's why these drives had data on them, b/c they were the original drives used w/ the first card.

---

### Post by jmg999 on 2010-07-25
It's in the process of building the array.  It's currently at 10%, but it appears to have been there for quite some time, so I'll continue to keep an eye on it.  In the meantime, I've contacted Promise support, and I'm expecting to hear from them in the next day or two.  I'll update this thread later today.

---

### Post by jmg999 on 2010-07-25
It appears to still be running.  Apparently, the webpam only reports in  10% increments.  It's at 30% right now, so it's going to be a while, but  it appears to be working properly.

---

### Post by bakegoodz on 2010-07-25
Looks to me that mdadm is failing /dev/sdb because there is problems with it. From the evidence of Smartmontools reporting the drive fine, and drive failing during raid building, I would say that the drive in question has bad sectors.

You could check it and zero it in one command with badblocks
example: badblocks -v -w -t 0 -p 0 /dev/sdb

If the test reports the drive ok, the zeroing may have made the drive remap those sectors and the drive may be fine for a while longer. If badblocks reports bad sectors, it usually means it is out of reserve sectors, or the drive is quickly deteriorating. I would junk it. To be thorough you could try 2 passes with badblocks if you really want to give the drive a chance remap bad sectors.

---

### Post by rubylaser on 2010-07-25
Bakegoodz, thanks for chiming in.  After having jmg999 do the SMART test, I should have had him do the bad blocks test.  Either your Promise controller is really slow to build arrays, or bakegoodz may be spot on.  I can *recently re-synced my whole array, and it took about 400 minutes with an AMD 4600+ X2.  If your Promise array fails to build properly he's correct.

---

### Post by jmg999 on 2010-07-25
The build got up to 73% and failed.  It said that drive 2 had become unplugged.  I have to say, this Promise card does not securely hold the SATA cables, and I don't have any locking cables on hand.  Anyhow, after fiddling w/ it (and in the process unplugging other drives), I was finally able to get all the drives plugged in properly, deleted the array, and restarted the build.  

As you can see from the log, there were multiple errors in building the array...

> 30 								SuperTrak EX8350 - Controller 1 								[COLOR=red]Error[/COLOR] 								2010/07/25 19:55:12 								Background Initialization on logical drive "/dev/md1" aborted at 73% because of error 							  							 								31 								SuperTrak EX8350 - Controller 1 								[COLOR=orange]Warning[/COLOR] 								2010/07/25 19:55:12 								Logical drive "/dev/md1" goes critical 							  							 								32 								SuperTrak EX8350 - Controller 1 								[COLOR=orange]Warning[/COLOR] 								2010/07/25 19:55:12 								Disk 2 unplugged 							  							 								33 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 19:29:11 								Background Initialization on logical drive "/dev/md1" 70% 							  							 								34 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 18:13:54 								Background Initialization on logical drive "/dev/md1" 60% 							  							 								35 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 17:00:22 								Background Initialization on logical drive "/dev/md1" 50% 							  							 								36 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 15:47:23 								Background Initialization on logical drive "/dev/md1" 40% 							  							 								37 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 14:33:56 								Background Initialization on logical drive "/dev/md1" 30% 							  							 								38 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 13:20:04 								Background Initialization on logical drive "/dev/md1" 20% 							  							 								39 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 12:17:59 								Disk error at LBA 0x06c8b336 on disk 4 fixed 							  							 								40 								SuperTrak EX8350 - Controller 1 								[COLOR=red]Error[/COLOR] 								2010/07/25 12:17:59 								BSL accessed on disk 4 at LBA 06c8b33641 								SuperTrak EX8350 - Controller 1 								[COLOR=orange]Warning[/COLOR] 								2010/07/25 12:17:59 								Task 20 disk error on disk 4 at LBA 0x06c8b336 (Length 0x1) with status 4051; Error register: 40 							  							 								42 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 12:14:08 								Disk error at LBA 0x068702a7 on disk 2 fixed 							  							 								43 								SuperTrak EX8350 - Controller 1 								[COLOR=red]Error[/COLOR] 								2010/07/25 12:14:08 								BSL accessed on disk 2 at LBA 068702a7 							  							 								44 								SuperTrak EX8350 - Controller 1 								[COLOR=orange]Warning[/COLOR] 								2010/07/25 12:14:08 								Task 20 disk error on disk 2 at LBA 0x068702a7 (Length 0x5c) with status 4051; Error register: 40 							  							 								45 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 12:13:59 								Disk error at LBA 0x068702a4 on disk 2 fixed 							  							 								46 								SuperTrak EX8350 - Controller 1 								[COLOR=red]Error[/COLOR] 								2010/07/25 12:13:59 								BSL accessed on disk 2 at LBA 068702a4 							  							 								47 								SuperTrak EX8350 - Controller 1 								[COLOR=orange]Warning[/COLOR] 								2010/07/25 12:13:59 								Task 20 disk error on disk 2 at LBA 0x068702a4 (Length 0x100) with status 4051; Error register: 40 							  							 								48 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 12:05:49 								Disk error at LBA 0x05f7a93d on disk 1 fixed 							  							 								49 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 12:05:46 								BSL log disk 1 at LBA 0x05f7a93a cleared 							  							 								50 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 12:05:46 								BSL update on disk 1 at LBA 0x05f7a93d 							  							 								51 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 12:05:46 								Disk error at LBA 0x05f7a93b on disk 1 fixed 							  							 								52 								SuperTrak EX8350 - Controller 1 								[COLOR=orange]Warning[/COLOR] 								2010/07/25 12:05:37 								Task 20 disk error on disk 1 at LBA 0x05f7a93b (Length 0xc5) with status 4051; Error register: 40 							  							 								53 								SuperTrak EX8350 - Controller 1 								[COLOR=red]Error[/COLOR] 								2010/07/25 12:05:27 								BSL accessed on disk 1 at LBA 05f7a93a 							  							 								54 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 12:05:27 								Disk error at LBA 0x05f7a938 on disk 1 fixed 							  							 								55 								SuperTrak EX8350 - Controller 1 								[COLOR=orange]Warning[/COLOR] 								2010/07/25 12:05:26 								Task 20 disk error on disk 1 at LBA 0x05f7a93a (Length 0xc7) with status 4051; Error register: 40 							  							 								56 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 12:05:26 								BSL update on disk 1 at LBA 0x05f7a938 							  							 								57 								SuperTrak EX8350 - Controller 1 								[COLOR=orange]Warning[/COLOR] 								2010/07/25 12:05:26 								Task 20 disk error on disk 1 at LBA 0x05f7a938 (Length 0x100) with status 4051; Error register: 40 							  							 								58 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 12:03:07 								Background Initialization on logical drive "/dev/md1" 10% 							  							 								59 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 11:31:41 								BSL log disk 8 at LBA 0x039496c0 cleared 							  							 								60 								SuperTrak EX8350 - Controller 1 								[COLOR=orange]Warning[/COLOR] 								2010/07/25 11:31:38 								Task 20 disk error on disk 8 at LBA 0x039496c0 (Length 0x43) with status 4051; Error register: 4061 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 11:31:32 								Disk error at LBA 0x039496bd on disk 8 fixed 							  							 								62 								SuperTrak EX8350 - Controller 1 								[COLOR=red]Error[/COLOR] 								2010/07/25 10:51:28 								BSL accessed on disk 2 at LBA 0f93a1e 							  							 								63 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 10:51:25 								BSL update on disk 2 at LBA 0x0f93a1e 							  							 								64 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 10:42:25 								BSL log disk 1 at LBA 0x0678ee7 cleared 							  							 								65 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 10:42:25 								BSL update on disk 1 at LBA 0x0678ee7 							  							 								66 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 10:42:16 								Disk error at LBA 0x0678edf on disk 1 fixed 							  							 								67 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 10:42:16 								BSL log disk 1 at LBA 0x0678edf cleared 							  							 								68 								SuperTrak EX8350 - Controller 1 								[COLOR=red]Error[/COLOR] 								2010/07/25 10:42:13 								BSL accessed on disk 1 at LBA 0678edf 							  							 								69 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 10:42:13 								BSL update on disk 1 at LBA 0x0678edf 							  							 								70 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 10:36:01 								Disk error at LBA 0x0c1c5e on disk 2 fixed 							  							 								71 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 10:36:01 								BSL log disk 2 at LBA 0x0c1c5e cleared 							  							 								72 								SuperTrak EX8350 - Controller 1 								[COLOR=red]Error[/COLOR] 								2010/07/25 10:36:01 								BSL accessed on disk 2 at LBA 0c1c5e 							  							 								73 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 10:36:01 								BSL update on disk 2 at LBA 0x0c1c5e 							  							 								74 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 10:35:55 								Disk error at LBA 0x0c1c5c on disk 2 fixed 							  							 								75 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 10:35:55 								BSL log disk 2 at LBA 0x0c1c5c cleared 							  							 								76 								SuperTrak EX8350 - Controller 1 								[COLOR=red]Error[/COLOR] 								2010/07/25 10:35:55 								BSL accessed on disk 2 at LBA 0c1c5c 							  							 								77 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 10:35:52 								BSL update on disk 2 at LBA 0x0c1c5c 							  							 								78 								SuperTrak EX8350 - Controller 1 								[COLOR=orange]Warning[/COLOR] 								2010/07/25 10:35:52 								Task 20 disk error on disk 2 at LBA 0x0c1c5c (Length 0x1) with status 4051; Error register: 40 							  							 								79 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 10:34:49 								Background Initialization on logical drive "/dev/md1" started 							  							 								80 								SuperTrak EX8350 - Controller 1 								[COLOR=blue]Information[/COLOR] 								2010/07/25 10:34:49 								Logical drive "/dev/md1" created

---

### Post by jmg999 on 2010-07-25
Sorry...that came out a mess, but you get the idea...hopefully. :)

I'm gonna see what happens this time around, but even if it builds properly, I don't have any faith in this card.  Even if it creates the array, I'm still gonna try Bakedgoodz's suggestion.

---

### Post by jmg999 on 2010-07-26
Well, it's still running.  12 hours later, and it's only at 51%.  My 7TB array managed by mdadm, and it only takes 12-13 hours in total.  I was given the choice of a fast or full initialization, and I chose full b/c of all the problems I've been having, but I don't recall the process taking this long the last time I had this array up and running.

---

### Post by rubylaser on 2010-07-26
I'll be surprised if it builds properly.  Maybe you had a bad connection before, but it sounds like you have a bad drive.  You might as well let it finish building and see if it works at this point.

---

### Post by jmg999 on 2010-07-26
Well, I got my reply from Promise...

I believe what you are looking for is a "pass-through" mode for the EX8350 which does not exist for this card, but supported in our latest offering.EX876x series.

---

### Post by jmg999 on 2010-07-26
Out of curiosity, is there a way to run badblocks, if the array's already been created?

---

### Post by jmg999 on 2010-07-27
It finally finished...over 20 hours later.  There were quite a few  errors on disk 1, but the error log says that they were all fixed.  I  just ran an fdisk, and the array doesn't show up.  However, /dev/sda  shows as one of the 500GB HDDs.  That's the only 500GB HDD that shows,  though.  The other seven aren't listed.

---

### Post by rubylaser on 2010-07-27
Sure you can run badblocks on a drive once the array has been created, just make sure the array, isn't mounted.  And, you could stop the array if you wanted to be extra safe.

```
badblocks -v -w -t 0 -p 0 /dev/sd<drive letter>
```

So, are you saying that mdadm is showing an 8 disk array with only 1 active hard drive or that your md1 array doesn't exist? 

What does

```
cat /proc/mdstat
```

show you?

---

### Post by jmg999 on 2010-07-27
mdadm isn't showing anything, b/c the Promise controller is managing this array.

> sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdi: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5745e6e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdi1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdj: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf8844ad1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdj1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdk: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x05563535

   Device Boot      Start         End      Blocks   Id  System
/dev/sdk1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdl: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc6603c74

   Device Boot      Start         End      Blocks   Id  System
/dev/sdl1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdm: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xff2ebb89

   Device Boot      Start         End      Blocks   Id  System
/dev/sdm1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdn: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5be14e4a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdn1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdo: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xbe4fb07e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdo1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdq: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b4bef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdq1               1         365     2931831   82  Linux swap / Solaris
/dev/sdq2             366       30401   241264170   83  Linux

Disk /dev/sdp: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7135fa61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdp1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/md0: 7001.4 GB, 7001415221248 bytes
2 heads, 4 sectors/track, 1709329888 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 458752 bytes
Disk identifier: 0x00000000 

As you can see, it's not showing /dev/sdb through /dev/sdh.  Yet, for some reason, it is showing /dev/sda.

---

### Post by bakegoodz on 2010-07-27
Yes, if you are using real hardware RAID, which that card should, it shows up as one device to Linux.
Hardware Raid will often completely fail consumer level hard drives when they develop bad sectors. In the past I have had failed drives check out fine, I would wipe them and put them back in and they would work after. Then I started buying Western Digital Raid Edition drives and stop having that problem. You now have enterprise or raid level drives with that don't take too long to remap bad sectors or Raid controllers will fail them.

---

### Post by jmg999 on 2010-07-27
If you look back at my fdisk posting, you'll see that it's only showing /dev/sda, and it's showing it at 500GB.  The array is 3.5TB, but it's not listing it.

---

### Post by bakegoodz on 2010-07-27
I have carefully read through all the postings in this thread, and I'm still perplexed by your problem.
 I have much experience with RAID, and I haven't seen anything like you are reporting. I have used hardware controllers from 3ware, Areca, and LSI and all of them make the RAID array only show one device to Linux.

So I think Linux is not detecting things correctly. There must some "Fake Raid" attributes to this card, even though I see it has a IOP333 RAID processor to handle raid stuff inside the card, because it still doesn't show the computer a single virtual drive like the adapters I'm familiar with. I searched to see if others have made this work, and  found a thread on this forum that had to compile a kernel module. [http://ubuntuforums.org/showthread.php?t=400858](http://ubuntuforums.org/showthread.php?t=400858) I think you have to have a 3rd party kernel driver to make this work, as I see the Ubuntu kernel doesn't name this series of adapters as having support.

---

### Post by jmg999 on 2010-07-27
Thanks for researching this for me. :)  I do appreciate it.  Just so you're aware, I did have this card up and running once before.  I used onboard RAID capabilities of the card to control the array.  After about 18 mos. or so, the card died on me, which was when I decided to make the switch to mdadm w/ my next array.  That was about 18 mos. ago.  This is the first time that I've put this card back online.  When I originally had it up and running, I don't recall anything special that I had to do to make it work.

---

### Post by jmg999 on 2010-07-27
I just deleted the array, and I'm gonna run badblocks on all the drives individually.  I'll post the results.

---

### Post by jmg999 on 2010-07-28
I let badblocks run all night, and these are the results...

> sudo badblocks -v -w -t 0 -p 0 /dev/sda
Checking for bad blocks in read-write mode
From block 0 to 488386583
Testing with pattern 0x00: done                                
Reading and comparing: done                                
Pass completed, 0 bad blocks found.

sudo badblocks -v -w -t 0 -p 0 /dev/sdb
Checking for bad blocks in read-write mode
From block 0 to 488386583
Testing with pattern 0x00: done                                
Reading and comparing: done                                
Pass completed, 0 bad blocks found.

sudo badblocks -v -w -t 0 -p 0 /dev/sdc
Checking for bad blocks in read-write mode
From block 0 to 488386583
Testing with pattern 0x00: done                                
Reading and comparing: done                                
Pass completed, 0 bad blocks found.

sudo badblocks -v -w -t 0 -p 0 /dev/sdd
Checking for bad blocks in read-write mode
From block 0 to 488386583
Testing with pattern 0x00: ^T
done                                
Reading and comparing: done                                
Pass completed, 0 bad blocks found.

sudo badblocks -v -w -t 0 -p 0 /dev/sde
Checking for bad blocks in read-write mode
From block 0 to 488386583
Testing with pattern 0x00: done                                
Reading and comparing: done                                
Pass completed, 0 bad blocks found.

sudo badblocks -v -w -t 0 -p 0 /dev/sdf
Checking for bad blocks in read-write mode
From block 0 to 488386583
Testing with pattern 0x00: done                                
Reading and comparing: done                                
Pass completed, 0 bad blocks found.

sudo badblocks -v -w -t 0 -p 0 /dev/sdg
Checking for bad blocks in read-write mode
From block 0 to 488386583
Testing with pattern 0x00: done                                
Reading and comparing: done                                
Pass completed, 0 bad blocks found.

sudo badblocks -v -w -t 0 -p 0 /dev/sdh
Checking for bad blocks in read-write mode
From block 0 to 488386583
Testing with pattern 0x00: done                                
Reading and comparing: done                                
Pass completed, 0 bad blocks found.

As you can clearly see, it didn't find anything wrong w/ any of the HDDs.  Just to be sure, I'd really like to run smartctl on the drives, but I can't seem to figure out how.

> sudo smartctl -d ata -H /dev/sda
smartctl version 5.38 [i686-pc-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Smartctl: Device Read Identity Failed (not an ATA/ATAPI device)

A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.

I looked at the manpage, and it made clear mention of using Smartctl on HDDs behind hardware RAID controllers, but it didn't specifically mention Promise, nor did the syntax look any different than what I was using.

---

### Post by jmg999 on 2010-07-28
I just called Promise, and they say that I should try two things:

1) delete all the partitions from all the HDDs
2) create the array w/ the Promise web tool, then run Parted on it

They say that they've seen instances, where Parted reports of the size of the array correctly, whereas fdisk doesn't.  I'll try it now, and report back in a bit.

---

### Post by jmg999 on 2010-07-28
So, odd turn of events...
 
 I recreated the array using the fast initialization process, which only  takes second.  I ran fdisk, but I still only saw /dev/sda at 500GB, so I  ran parted on it and created a GPT partition the size of the array  (3.5TB).  I then looked at fdisk again, but it still only showed  /dev/sda at 500GB, so I ran fdisk on /dev/sda and deleted the GPT  partition, or at least, I thought I did.  I know that fdisk doesn't work  well w/ GPT, but it didn't error out or give a warning of any kind.  I  then ran fdisk again, and sure enough, it showed /dev/sda at 3.5TB.  I'm  not sure why or how, but here's the fdisk readout...
 
 >  sudo fdisk -l
 
 WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.
 
 
 Disk /dev/sda: 3500.0 GB, 3499999756288 bytes
 255 heads, 63 sectors/track, 425517 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disk identifier: 0x00000000
 
    Device Boot      Start         End      Blocks   Id  System

---

### Post by bakegoodz on 2010-08-05
I believe the whole size reporting issue is with fdisk, if it doesn't support GPT partitions at all it may not even have the right internal code to calculate byte sizes above 2 TB.

Maybe try creating the software raid again with mdadm.
 If it still doesn't work maybe something is wrong with the way you can access the individual drives through the Raid card. Promise said themselves that it doesn't support pass-through mode. It is a mystery how you have pass-though access to the drives.

---

