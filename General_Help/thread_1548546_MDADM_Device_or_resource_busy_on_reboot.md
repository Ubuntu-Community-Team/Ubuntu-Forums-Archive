---
title: "MDADM Device or resource busy on reboot"
date: 2010-08-08
forum: General Help
---

### Post by Cyrex056 on 2010-08-08
Hi All,

Last night, during shutdown, my computer decided to take a very long time shutting down for some reason.  When I rebooted it today, I got a cannot mount /dev/md0 (Device or resource busy. Wait, skip, or manual).  I'm running Lucid.  It's a Raid 6 system.  I've tried

sudo mdadm --assemble --scan  --verbose

Output:

mdadm: looking for devices for /dev/md0
mdadm: no RAID superblock on /dev/sdf
mdadm: /dev/sdf has wrong uuid.
mdadm: no RAID superblock on /dev/sde
mdadm: /dev/sde has wrong uuid.
mdadm: no RAID superblock on /dev/sdd
mdadm: /dev/sdd has wrong uuid.
mdadm: no RAID superblock on /dev/sdb
mdadm: /dev/sdb has wrong uuid.
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdc has wrong uuid.
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: /dev/sda5 has wrong uuid.
mdadm: no RAID superblock on /dev/sda2
mdadm: /dev/sda2 has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has wrong uuid.
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has wrong uuid.
mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 4.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 1.
mdadm: added /dev/sdd1 to /dev/md0 as 0
mdadm: added /dev/sdc1 to /dev/md0 as 1
mdadm: added /dev/sde1 to /dev/md0 as 3
mdadm: added /dev/sdf1 to /dev/md0 as 4
mdadm: added /dev/sdb1 to /dev/md0 as 2
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.
mdadm: looking for devices for /dev/md0
mdadm: no RAID superblock on /dev/sdf
mdadm: /dev/sdf has wrong uuid.
mdadm: no RAID superblock on /dev/sde
mdadm: /dev/sde has wrong uuid.
mdadm: no RAID superblock on /dev/sdd
mdadm: /dev/sdd has wrong uuid.
mdadm: no RAID superblock on /dev/sdb
mdadm: /dev/sdb has wrong uuid.
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdc has wrong uuid.
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: /dev/sda5 has wrong uuid.
mdadm: no RAID superblock on /dev/sda2
mdadm: /dev/sda2 has wrong uuid.
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has wrong uuid.
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sda has wrong uuid.
mdadm: /dev/sdf1 is identified as a member of /dev/md0, slot 4.
mdadm: /dev/sde1 is identified as a member of /dev/md0, slot 3.
mdadm: /dev/sdd1 is identified as a member of /dev/md0, slot 0.
mdadm: /dev/sdb1 is identified as a member of /dev/md0, slot 2.
mdadm: /dev/sdc1 is identified as a member of /dev/md0, slot 1.
mdadm: added /dev/sdd1 to /dev/md0 as 0
mdadm: added /dev/sdc1 to /dev/md0 as 1
mdadm: added /dev/sde1 to /dev/md0 as 3
mdadm: added /dev/sdf1 to /dev/md0 as 4
mdadm: added /dev/sdb1 to /dev/md0 as 2
mdadm: /dev/md0 assembled from 1 drive - not enough to start the array.
mdadm: looking for devices for further assembly
mdadm: cannot open device /dev/sdf1: Device or resource busy
mdadm: cannot open device /dev/sdf: Device or resource busy
mdadm: cannot open device /dev/sde1: Device or resource busy
mdadm: cannot open device /dev/sde: Device or resource busy
mdadm: cannot open device /dev/sdd1: Device or resource busy
mdadm: cannot open device /dev/sdd: Device or resource busy
mdadm: cannot open device /dev/sdb1: Device or resource busy
mdadm: cannot open device /dev/sdb: Device or resource busy
mdadm: cannot open device /dev/sdc1: Device or resource busy
mdadm: cannot open device /dev/sdc: Device or resource busy
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: no recogniseable superblock on /dev/sda2
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
elfndragon@huston-desktop:~$ 


I have searched around ubuntuforums and google, but the steps do not appear to work for me.  Are there any masochists out there that want to help me tackle this? :D

The data on the Raid Array is very inportant to me, and I would not like to lose it.  Is there any way to get it back?

---

### Post by Cyrex056 on 2010-08-09
Readout of /proc/mdstat gives:

elfndragon@huston-desktop:~$ cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md0 : inactive sdb1[2](S) sdf1[4](S) sde1[3](S) sdc1[1](S) sdd1[0](S)
      4883799680 blocks
       
unused devices: <none>


If that helps...

---

### Post by rubylaser on 2010-08-09
It looks like it's trying to add /dev/sda1 and /dev/sda2 to the array.  Have you ran smartmontools (to verify SMART status)?

```
sudo apt-get install smartmontools badblocks
```

And to test the disk

```
smartctl -d ata -H /dev/sda
```

Also, can you paste the output of

```
sudo fdisk -l
```

Also, have you tried to assemble the array by actually giving it the disks in the array and forcing it like this?

```
sudo mdadm --assemble --run --force /dev/md0 /dev/sd[abdef]1
```

---

### Post by Cyrex056 on 2010-08-09
I have run smartmontools to verify SMART status.  All drives passed.

The output of sudo fdisk -l is as follows:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001c159

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e1585

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a7d33

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      118617   952791021   83  Linux
/dev/sdc2          118618      121601    23968980    5  Extended
/dev/sdc5          118618      121601    23968948+  82  Linux swap / Solaris

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00061da3

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000046b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00092072

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      121601   976760001   fd  Linux raid autodetect

********************************************************************

I ran the command "sudo mdadm --assemble --run --force /dev/md0 /dev/sd[abdef]1" and the output was:

mdadm: forcing event count in /dev/sda1(1) from 2471 upto 2474
mdadm: forcing event count in /dev/sdb1(0) from 2470 upto 2474
mdadm: /dev/md0 has been started with 3 drives (out of 5).

I then did a quick cat /proc/mdstat and the array is recovering from a degraded state.  These HDs are not quite a year old.  Smartmontools said that the drives passed.  Ubuntu states that /dev/sda and /dev/sdb are on a Promise controller card, while the others are connected to the motherboard.  Could that be causing a problem?  Would it be better if all of the drives in the RAID were on one SATA controller card?

The problem occurred seemingly because Ubuntu took forever to shut down.  I don't know where to find logs to determine if there was an error somewhere, but I would like to try to find out, since I don't want to have to go through this again.

Thank you so much, rubylaser!! You get a million cookies (or treat of your choice)! :KS  :D

---

### Post by Cyrex056 on 2010-08-09
Actually, I suppose I posted too soon.  So the reassembly was approximately 33% done, when I checked it with cat /proc/mdstat and it said that 4 out of 5 drives were failed.

Now when I try "sudo mdadm --assemble --run --force /dev/md0 /dev/sda1 /dev/sdb1 /dev/sdd1 /dev/sde1 /dev/sdf1" is gives me:

mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: /dev/sda1 has no superblock - assembly aborted

Also, the output of sudo fdisk -l changed to:

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a7d33

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      118617   952791021   83  Linux
/dev/sda2          118618      121601    23968980    5  Extended
/dev/sda5          118618      121601    23968948+  82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001c159

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000046b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e1585

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00061da3

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00092072

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      121601   976760001   fd  Linux raid autodetect

So now I'm running "sudo mdadm --assemble --run --force /dev/md0 /dev/sdb1 /dev/sdc1 /dev/sdd1 /dev/sde1 /dev/sdf1".  It's attempting to rebuild again.  Why are my drive designations changing?

Please help  :(

---

### Post by Cyrex056 on 2010-08-10
And also for some reason the smart code you told me to use outputs the following for both /dev/sdc and /dev/sdd:

smartctl version 5.38 [x86_64-unknown-linux-gnu] Copyright (C) 2002-8 Bruce Allen
Home page is [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Smartctl: Device Read Identity Failed (not an ATA/ATAPI device)

A mandatory SMART command failed: exiting. To continue, add one or more '-T permissive' options.

None of this makes sense to me.

---

### Post by rubylaser on 2010-08-10
Ahh, a Promise card :)  Read through this thread I was posting in a few weeks ago...
[http://ubuntuforums.org/showthread.php?t=1538207]("http://ubuntuforums.org/showthread.php?t=1538207")  Again, a Promise card causing the same sort of behavior with mdadm.


And smartmontools won't work the way I showed you behind a RAID card, you'll need to query them like this...
```
sudo smartctl -H /dev/sda
sudo smartctl -H /dev/sdb
```

What type of Promise card do you have?

I use Supermicro's controller cards for mdadm, and they work great.  They both support up to 8 hard drives.

**PCI-X Card**
[http://www.provantage.com/supermicro-aoc-sat2-mv8~7SUPM0X9.htm]("http://www.provantage.com/supermicro-aoc-sat2-mv8~7SUPM0X9.htm")

**PCI Express x4**
[http://www.provantage.com/supermicro-aoc-saslp-mv8~7SUP918N.htm]("http://www.provantage.com/supermicro-aoc-saslp-mv8~7SUP918N.htm")

---

### Post by Cyrex056 on 2010-08-10
OH lovely. :rolleyes:

The card I have is a Promise SATA300 TX4 PCI 4-Port Adapter.

I'll try the new smartctl code when I get back to that machine.

So if I buy your recommendations, would it still be possible to rebuild the array?  I'm not afraid to spend money to get my data back :)[]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816102065")

---

### Post by Cyrex056 on 2010-08-10
The output of:

sudo smartctl -H /dev/sdX

for the HDs on the Promise card indicate that they passed.

So I guess there's a problem with the Promise card, right?

---

### Post by Cyrex056 on 2010-08-12
Well my new hard drive controller card came yesterday.  I installed it and hooked up the drives.  I then forced MDADM to rebuild the array, which is did with 4 out of 5 disks, I then manually added the 5th disk.  So everything is back to normal! YAAY!!

Thanks again, Rubylaser!  Your help is very much appreciated!

One last thing, when I do an fdisk -l now, the output is as follows:


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e1585

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001c159

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00061da3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a7d33

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1      118617   952791021   83  Linux
/dev/sdd2          118618      121601    23968980    5  Extended
/dev/sdd5          118618      121601    23968948+  82  Linux swap / Solaris

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000046b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00092072

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      121601   976760001   fd  Linux raid autodetect

Disk /dev/md0: 3000.6 GB, 3000606523392 bytes
2 heads, 4 sectors/track, 732569952 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 196608 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

*********************

/dev/md0 doesn't contain a valid partition table....that's normal, right?  Since it's the Raid disk?

---

