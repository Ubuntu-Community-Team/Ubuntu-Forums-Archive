---
title: "Failed to mount Raid(5) - Raid not active help!"
date: 2011-07-25
forum: General Help
---

### Post by JaizEdelmann on 2011-07-25
Hey everyone, so i had to take a part my mediacenter yesterday and i assembled it again, and now ubuntu wont let me mount my raid5 so ubuntu wont boot up, unless i go into maintance og skip mounting of the raid.

I though it might be because i swapped around on some sata cabels but i've triede the combinations that would make sense for them to have been in but still it fails.

My raid contains 4x2TB discs from WD and are realtively new so i would find it odd if one allready have broken. What can i do? Kinda panic in the hole household now since we use the mediacenter across rooms and family members, so any help would be much appreciated :)
 
> 
jaiz@mediabox:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : inactive sde1[4](S) sdd1[1](S) sdc1[0](S) sdf1[2](S)
      7814047744 blocks

unused devices: <none>

fdisk
>   Disk /dev/sdc: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0d8ed89b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x90a3cf5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6320ada9

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      243201  1953512001   fd  Linux raid autodetect

Disk /dev/sdf: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x026198bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      243201  1953512001   fd  Linux raid autodetect



---

### Post by JaizEdelmann on 2011-07-25
Following things tried:


jaiz@mediabox:~$ sudo mdadm -A /dev/md0
> mdadm: metadata format 00.90 unknown, ignored.
mdadm: SET_ARRAY_INFO failed for /dev/md0: Device or resource busy



jaiz@mediabox:~$ sudo mdadm -A -s --force
> mdadm: metadata format 00.90 unknown, ignored.
mdadm: forcing event count in /dev/sdc1(0) from 1242 upto 1248
mdadm: forcing event count in /dev/sdd1(1) from 1242 upto 1248
mdadm: /dev/md0 has been started with 3 drives (out of 4) and 1 spare.
/dev/md0: File exists
mdadm: /dev/md/0 already active, cannot restart it!
mdadm:   /dev/md/0 needed for /dev/sde1...


Edit2: So after the following i triede rebooting and the raid started up? unsure if this was random , or something actually worked. 
Edit3: Rebooted a few times more just to make sure, seems like the raid just works now?

---

### Post by JaizEdelmann on 2011-07-26
Think the raid had trouble reading some files today so decided to reboot and I got inactive raid again had to use force command again to get up and running could really use some help finding the problem when I used the command it said something about using alcorythm 2


Edit mediastream on the raid need to buffer and take extremely long time to render :s

---

### Post by JaizEdelmann on 2011-07-26
Allright i've been digging abit again today:

when i do cat/proc/mdstat today i get:

```
jaiz@mediabox:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md0 : active raid5 sdc1[0] sdd1[1] sdf1[2]
      5860535808 blocks level 5, 64k chunk, algorithm 2 [4/3] [UUU_]
```

And i know sde1 is part of the raid i do not see the disc in the raid so i would assume thats the disc thats creating the problem, however if i do

sudo fdisk -l
```
Disk /dev/sde: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6320ada9

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      243201  1953512001   fd  Linux raid autodetect

```

So the harddrive seems to broken in terms of raid, but the harddrive is detected by fdisk, what is my next step?

---

### Post by JaizEdelmann on 2011-07-28
Allright after some days of digging around i found out that my hdd was indeed broken, so i used the failed mdadm command and remove on my disc, now i shutdown the machine add'd my new drive and wanted to add it but now i got this error, and i've been stuck here the last 4 hours :( need some help! badly :)

jaiz@mediabox:~$ sudo mdadm --manage /dev/md0 -a /dev/sdf1

> mdadm: metadata format 00.90 unknown, ignored.
mdadm: cannot get array info for /dev/md0


If i try and do:

sudo mdadm --create --assume-clean --level=5 --raid-devices=4 /dev/md0 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1
> mdadm: metadata format 00.90 unknown, ignored.
mdadm: /dev/sdc1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Sat Mar 26 01:43:41 2011
mdadm: /dev/sdd1 appears to contain an ext2fs file system
    size=1565568512K  mtime=Wed Jul 27 00:46:14 2011
mdadm: /dev/sdd1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Sat Mar 26 01:43:41 2011
mdadm: /dev/sde1 appears to contain an ext2fs file system
    size=1297133056K  mtime=Wed Jul 27 00:46:14 2011
mdadm: /dev/sde1 appears to be part of a raid array:
    level=raid5 devices=4 ctime=Sat Mar 26 01:43:41 2011
Continue creating array? n
mdadm: create aborted.


As you can see it doesent understand sdf should be integrated into the array, and instead adds sdd1 twice :S

---

