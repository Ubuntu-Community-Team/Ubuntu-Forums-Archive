---
title: "all drives but 1 marked as spares in mdadm raid"
date: 2012-05-25
forum: General Help
---

### Post by jgrevich on 2012-05-25
I was trying to install another SATA controller (RockRaid 622) following the instructions here: [https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)

I followed the shortcut and installed the 1.1 .deb package.  I did not see the card in lspci and noticed that I did not follow the part of instructions that added rr622x to /etc/initramfs-tools/modules.  I did so and ran update-initramfs -u and rebooted the computer.  Doing so made things worse and hung the startup.  I rebooted to a previous kernel build, removed the package with dpkr -r rr622x, and removed the line I added to /etc/initramfs-tools/modules.  Upon the subsequent reboot it still hung at initramfs or at a purple screen; either way I had to type exit to continue.

Whatever I did now prevented one of my RAID arrays from assembling.  It thinks there are 6 spares and 1 drive.  I can verify that all 7 drives are healthy.  I tried `mdadm --stop /dev/md127` and `mdadm --assemble /dev/md127 /dev/sd[bcdeghf]1` but it yielded:

mdadm: superblock on /dev/sdf1 doesn't match others - assembly aborted

Below are the results for mdadm -E on all of the involved drives.  Any idea how to resolve this problem?

```

root@jhtpc:~# mdadm -E /dev/sdb
/dev/sdb:
   MBR Magic : aa55
Partition[0] :   3907024002 sectors at           63 (type fd)
root@jhtpc:~# mdadm -E /dev/sdb1
/dev/sdb1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6eab8764:eefb81c1:2bc311fd:f2625219
           Name : :jhtpc
  Creation Time : Sat Jul 30 12:41:31 2011
     Raid Level : -unknown-
   Raid Devices : 0

 Avail Dev Size : 3907021954 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 7ae4d84e:b10360f4:2ffa376b:c073db75

    Update Time : Thu May 24 20:34:55 2012
       Checksum : ed363c27 - correct
         Events : 1


   Device Role : spare
   Array State :  ('A' == active, '.' == missing)
root@jhtpc:~# mdadm -E /dev/sdc1
/dev/sdc1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6eab8764:eefb81c1:2bc311fd:f2625219
           Name : :jhtpc
  Creation Time : Sat Jul 30 12:41:31 2011
     Raid Level : -unknown-
   Raid Devices : 0

 Avail Dev Size : 3907021954 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 984e280b:a912f072:0eb7b6ac:e8bb0e9c

    Update Time : Thu May 24 20:34:55 2012
       Checksum : 8fc7ba43 - correct
         Events : 1


   Device Role : spare
   Array State :  ('A' == active, '.' == missing)
root@jhtpc:~# mdadm -E /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6eab8764:eefb81c1:2bc311fd:f2625219
           Name : :jhtpc
  Creation Time : Sat Jul 30 12:41:31 2011
     Raid Level : -unknown-
   Raid Devices : 0

 Avail Dev Size : 3907021954 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 46f2527c:35bc5fc7:3a93be09:a054b884

    Update Time : Thu May 24 20:34:55 2012
       Checksum : 9b137c60 - correct
         Events : 1


   Device Role : spare
   Array State :  ('A' == active, '.' == missing)
root@jhtpc:~# mdadm -E /dev/sde1
/dev/sde1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6eab8764:eefb81c1:2bc311fd:f2625219
           Name : :jhtpc
  Creation Time : Sat Jul 30 12:41:31 2011
     Raid Level : -unknown-
   Raid Devices : 0

 Avail Dev Size : 3907021954 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : 93e95ee9:af42a5dc:e43a8cf6:fb5a3990

    Update Time : Thu May 24 20:34:55 2012
       Checksum : 15b3a82d - correct
         Events : 1


   Device Role : spare
   Array State :  ('A' == active, '.' == missing)
root@jhtpc:~# mdadm -E /dev/sdf1
/dev/sdf1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 6eab8764:eefb81c1:2bc311fd:f2625219
           Name : :jhtpc
  Creation Time : Sat Jul 30 12:41:31 2011
     Raid Level : raid6
   Raid Devices : 7

 Avail Dev Size : 3907021954 (1863.01 GiB 2000.40 GB)
     Array Size : 19535104000 (9315.06 GiB 10001.97 GB)
  Used Dev Size : 3907020800 (1863.01 GiB 2000.39 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : clean
    Device UUID : 19e6e111:278f0937:29e8ff09:cfffa8d6

Internal Bitmap : 8 sectors from superblock
    Update Time : Thu May 24 19:26:32 2012
       Checksum : f295d01f - correct
         Events : 23301

         Layout : left-symmetric
     Chunk Size : 512K

   Device Role : Active device 6
   Array State : AAAAAAA ('A' == active, '.' == missing)
root@jhtpc:~# mdadm -E /dev/sdg1
/dev/sdg1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6eab8764:eefb81c1:2bc311fd:f2625219
           Name : :jhtpc
  Creation Time : Sat Jul 30 12:41:31 2011
     Raid Level : -unknown-
   Raid Devices : 0

 Avail Dev Size : 3907021954 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : ee61672a:8bcdf632:dca3a796:18f37c5e

    Update Time : Thu May 24 20:34:55 2012
       Checksum : 1b6cac7c - correct
         Events : 1


   Device Role : spare
   Array State :  ('A' == active, '.' == missing)
root@jhtpc:~# mdadm -E /dev/sdh1
/dev/sdh1:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x0
     Array UUID : 6eab8764:eefb81c1:2bc311fd:f2625219
           Name : :jhtpc
  Creation Time : Sat Jul 30 12:41:31 2011
     Raid Level : -unknown-
   Raid Devices : 0

 Avail Dev Size : 3907021954 (1863.01 GiB 2000.40 GB)
    Data Offset : 2048 sectors
   Super Offset : 8 sectors
          State : active
    Device UUID : ad0962eb:2c324474:a63f3e3a:33cabad6

    Update Time : Thu May 24 20:34:55 2012
       Checksum : 39892bc1 - correct
         Events : 1


   Device Role : spare
   Array State :  ('A' == active, '.' == missing)

```

Here is other useful info:

Cannot assemble since it thinks the superblock doesn't match.
```

root@jhtpc:~# mdadm --assemble /dev/md127 /dev/sd[bcdeghf]1
mdadm: superblock on /dev/sdf1 doesn't match others - assembly aborted

```

Excluding sdf allows it to assemble an array of 6 spares. WTF?
```

root@jhtpc:~# mdadm --assemble /dev/md127 /dev/sd[bcdegh]1
mdadm: /dev/md127 assembled from 0 drives and 6 spares - not enough to start the array.

```


```

root@jhtpc:~# cat /proc/mdstat 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md127 : inactive sdb1[3](S) sdh1[4](S) sdg1[5](S) sde1[0](S) sdd1[1](S) sdc1[2](S)
      11721065862 blocks super 1.2

```

---

### Post by jgrevich on 2012-05-25
I read elsewhere that someone fixed a similar problem by removing the superblocks from the other drives (in my case, all but sdf).  Then he ran mdadm --asemble with --update=resync ([http://www.storageforum.net/forum/showthread.php/5890-RAID-Superblock-disappeared-from-one-of-my-disks-after-crash-Fix](http://www.storageforum.net/forum/showthread.php/5890-RAID-Superblock-disappeared-from-one-of-my-disks-after-crash-Fix))

Here are the results of mdadm --assemble --scan -v

```

root@jhtpc:~# mdadm --assemble --scan -v
mdadm: looking for devices for /dev/md/eir
mdadm: cannot open device /dev/md/eir: Device or resource busy
mdadm: cannot open device /dev/sdr1: Device or resource busy
mdadm: cannot open device /dev/sdr: Device or resource busy
mdadm: cannot open device /dev/sdq1: Device or resource busy
mdadm: cannot open device /dev/sdq: Device or resource busy
mdadm: cannot open device /dev/sdp1: Device or resource busy
mdadm: cannot open device /dev/sdp: Device or resource busy
mdadm: cannot open device /dev/sdo1: Device or resource busy
mdadm: cannot open device /dev/sdo: Device or resource busy
mdadm: cannot open device /dev/sdn1: Device or resource busy
mdadm: cannot open device /dev/sdn: Device or resource busy
mdadm: cannot open device /dev/sdm1: Device or resource busy
mdadm: cannot open device /dev/sdm: Device or resource busy
mdadm: cannot open device /dev/sdl1: Device or resource busy
mdadm: cannot open device /dev/sdl: Device or resource busy
mdadm: cannot open device /dev/sdk1: Device or resource busy
mdadm: cannot open device /dev/sdk: Device or resource busy
mdadm: cannot open device /dev/sdj1: Device or resource busy
mdadm: cannot open device /dev/sdj: Device or resource busy
mdadm: cannot open device /dev/sdi1: Device or resource busy
mdadm: cannot open device /dev/sdi: Device or resource busy
mdadm: /dev/sdh1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdh
mdadm: /dev/sdg1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdg
mdadm: cannot open device /dev/sr0: No medium found
mdadm: cannot open device /dev/sdf1: Device or resource busy
mdadm: cannot open device /dev/sdf: Device or resource busy
mdadm: /dev/sde1 has wrong uuid.
mdadm: no RAID superblock on /dev/sde
mdadm: /dev/sdd1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdd
mdadm: /dev/sdc1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdc
mdadm: /dev/sdb1 has wrong uuid.
mdadm: no RAID superblock on /dev/sdb
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: no RAID superblock on /dev/sda2
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: looking for devices for /dev/md/jhtpc
mdadm: cannot open device /dev/md/eir: Device or resource busy
mdadm: cannot open device /dev/sdr1: Device or resource busy
mdadm: cannot open device /dev/sdr: Device or resource busy
mdadm: cannot open device /dev/sdq1: Device or resource busy
mdadm: cannot open device /dev/sdq: Device or resource busy
mdadm: cannot open device /dev/sdp1: Device or resource busy
mdadm: cannot open device /dev/sdp: Device or resource busy
mdadm: cannot open device /dev/sdo1: Device or resource busy
mdadm: cannot open device /dev/sdo: Device or resource busy
mdadm: cannot open device /dev/sdn1: Device or resource busy
mdadm: cannot open device /dev/sdn: Device or resource busy
mdadm: cannot open device /dev/sdm1: Device or resource busy
mdadm: cannot open device /dev/sdm: Device or resource busy
mdadm: cannot open device /dev/sdl1: Device or resource busy
mdadm: cannot open device /dev/sdl: Device or resource busy
mdadm: cannot open device /dev/sdk1: Device or resource busy
mdadm: cannot open device /dev/sdk: Device or resource busy
mdadm: cannot open device /dev/sdj1: Device or resource busy
mdadm: cannot open device /dev/sdj: Device or resource busy
mdadm: cannot open device /dev/sdi1: Device or resource busy
mdadm: cannot open device /dev/sdi: Device or resource busy
mdadm: no RAID superblock on /dev/sdh
mdadm: no RAID superblock on /dev/sdg
mdadm: cannot open device /dev/sr0: No medium found
mdadm: cannot open device /dev/sdf1: Device or resource busy
mdadm: cannot open device /dev/sdf: Device or resource busy
mdadm: no RAID superblock on /dev/sde
mdadm: no RAID superblock on /dev/sdd
mdadm: no RAID superblock on /dev/sdc
mdadm: no RAID superblock on /dev/sdb
mdadm: cannot open device /dev/sda5: Device or resource busy
mdadm: no RAID superblock on /dev/sda2
mdadm: cannot open device /dev/sda1: Device or resource busy
mdadm: cannot open device /dev/sda: Device or resource busy
mdadm: /dev/sdh1 is identified as a member of /dev/md/jhtpc, slot -1.
mdadm: /dev/sdg1 is identified as a member of /dev/md/jhtpc, slot -1.
mdadm: /dev/sde1 is identified as a member of /dev/md/jhtpc, slot -1.
mdadm: /dev/sdd1 is identified as a member of /dev/md/jhtpc, slot -1.
mdadm: /dev/sdc1 is identified as a member of /dev/md/jhtpc, slot -1.
mdadm: /dev/sdb1 is identified as a member of /dev/md/jhtpc, slot -1.
mdadm: added /dev/sdg1 to /dev/md/jhtpc as -1
mdadm: added /dev/sde1 to /dev/md/jhtpc as -1
mdadm: added /dev/sdd1 to /dev/md/jhtpc as -1
mdadm: added /dev/sdc1 to /dev/md/jhtpc as -1
mdadm: added /dev/sdb1 to /dev/md/jhtpc as -1
mdadm: added /dev/sdh1 to /dev/md/jhtpc as -1
mdadm: /dev/md/jhtpc assembled from 0 drives and 6 spares - not enough to start the array.

```

---

### Post by jgrevich on 2012-05-25
I'm thinking of recreating the array. How can I be sure to do this without affecting the data?  From what I understand, the order of the drives is important.  Any place where I can get that info?

```

root@jhtpc:~# mdadm --create /dev/md127 -v -l 6 -n 7 /dev/sd[bcdefgh]1 --assume-clean
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: chunk size defaults to 512K
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdf1 appears to be part of a raid array:
    level=raid6 devices=7 ctime=Sat Jul 30 12:41:31 2011
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdg1 appears to be part of a raid array:
    level=-unknown- devices=0 ctime=Sat Jul 30 12:41:31 2011
mdadm: layout defaults to left-symmetric
mdadm: /dev/sdh1 appears to be part of a raid array:
    level=-unknown- devices=0 ctime=Sat Jul 30 12:41:31 2011
mdadm: size set to 1953510400K
Continue creating array? n
mdadm: create aborted.

```

---

### Post by jgrevich on 2012-05-25
I found this in an old syslog:

```

May 21 01:44:27 localhost kernel: [   13.506808] md/raid:md127: device sdg1 operational as raid disk 5
May 21 01:44:27 localhost kernel: [   13.506810] md/raid:md127: device sdc1 operational as raid disk 2
May 21 01:44:27 localhost kernel: [   13.506811] md/raid:md127: device sdh1 operational as raid disk 4
May 21 01:44:27 localhost kernel: [   13.506813] md/raid:md127: device sde1 operational as raid disk 0
May 21 01:44:27 localhost kernel: [   13.506815] md/raid:md127: device sdf1 operational as raid disk 6
May 21 01:44:27 localhost kernel: [   13.506816] md/raid:md127: device sdd1 operational as raid disk 1
May 21 01:44:27 localhost kernel: [   13.506818] md/raid:md127: device sdb1 operational as raid disk 3
May 21 01:44:27 localhost kernel: [   13.507096] md/raid:md127: allocated 7436kB
May 21 01:44:27 localhost kernel: [   13.507109] md/raid:md127: raid level 6 active with 7 out of 7 devices, algorithm 2
May 21 01:44:27 localhost kernel: [   13.507111] RAID conf printout:
May 21 01:44:27 localhost kernel: [   13.507112]  --- level:6 rd:7 wd:7
May 21 01:44:27 localhost kernel: [   13.507113]  disk 0, o:1, dev:sde1
May 21 01:44:27 localhost kernel: [   13.507115]  disk 1, o:1, dev:sdd1
May 21 01:44:27 localhost kernel: [   13.507116]  disk 2, o:1, dev:sdc1
May 21 01:44:27 localhost kernel: [   13.507117]  disk 3, o:1, dev:sdb1
May 21 01:44:27 localhost kernel: [   13.507118]  disk 4, o:1, dev:sdh1
May 21 01:44:27 localhost kernel: [   13.507119]  disk 5, o:1, dev:sdg1
May 21 01:44:27 localhost kernel: [   13.507121]  disk 6, o:1, dev:sdf1
May 21 01:44:27 localhost kernel: [   13.507228] created bitmap (15 pages) for device md127
May 21 01:44:27 localhost kernel: [   13.507560] md127: bitmap initialized from disk: read 1/1 pages, set 0 of 29809 bits
May 21 01:44:27 localhost kernel: [   13.521918] md127: detected capacity change from 0 to 10001973248000
May 21 01:44:27 localhost kernel: [   13.522918]  md127: unknown partition table

```

Given the above info, is it correct that I should modify my mdadm --create command with the drive order below:

```

mdadm --create /dev/md127 -v -l 6 -n 7 /dev/sd[edcbhgf]1 --assume-clean

```

---

### Post by jgrevich on 2012-05-25
This tremendous post gave me the confidence to go forward with wiping the superblocks and re-creating the raid: [http://serverfault.com/questions/347606/recover-raid-5-data-after-created-new-array-instead-of-re-using](http://serverfault.com/questions/347606/recover-raid-5-data-after-created-new-array-instead-of-re-using)

At first it didn't work since it seems that `mdadm --create /dev/md127 -v -l 6 -n 7 /dev/sd[edcbhgf]1 --assume-clean` does not abide by the drive order given within the [].  Checking the filesystem with `fsck.ext4 /dev/md127` failed.  I had to stop the array and recreate once more using the following commands:

```

mdadm --zero-superblock /dev/sd[bcdefgh]1
mdadm --create -v -l 6 -n 7 --assume-clean /dev/md127 /dev/sde1 /dev/sdd1 /dev/sdc1 /dev/sdb1 /dev/sdh1 /dev/sdg1 /dev/sdf1

```

`cat /proc/mdstat` yielded a happy array.  `fsck.ext4 /dev/md127` yielded a happy filesystem (e.g. correct drive order).  I am now checking the array's integrity with `/usr/share/mdadm/checkarray /dev/md127`.

I'll report the status after the verification is complete. So far so good:

```

Every 1.0s: cat /proc/mdstat                                                                                                                                                 Fri May 25 02:44:10 2012

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid6 sdf1[6] sdg1[5] sdh1[4] sdb1[3] sdc1[2] sdd1[1] sde1[0]
      9767552000 blocks super 1.2 level 6, 512k chunk, algorithm 2 [7/7] [UUUUUUU]
      [==>..................]  check = 10.2% (199343504/1953510400) finish=372.0min speed=78572K/sec

```

---

### Post by jgrevich on 2012-05-25
Check ran fine and I'm back in business. I would have sweated a lot more bullets if I didn't have a 2wk old backup of this dataset on another system.  Thank you mdadm for being so flexible.

---

### Post by jimmah6786 on 2012-12-22
> **jgrevich said:**
> This tremendous post gave me the confidence to go forward with wiping the superblocks and re-creating the raid: [http://serverfault.com/questions/347606/recover-raid-5-data-after-created-new-array-instead-of-re-using](http://serverfault.com/questions/347606/recover-raid-5-data-after-created-new-array-instead-of-re-using)

At first it didn't work since it seems that `mdadm --create /dev/md127 -v -l 6 -n 7 /dev/sd[edcbhgf]1 --assume-clean` does not abide by the drive order given within the [].  Checking the filesystem with `fsck.ext4 /dev/md127` failed.  I had to stop the array and recreate once more using the following commands:

```

mdadm --zero-superblock /dev/sd[bcdefgh]1
mdadm --create -v -l 6 -n 7 --assume-clean /dev/md127 /dev/sde1 /dev/sdd1 /dev/sdc1 /dev/sdb1 /dev/sdh1 /dev/sdg1 /dev/sdf1

```


`cat /proc/mdstat` yielded a happy array.  `fsck.ext4 /dev/md127` yielded a happy filesystem (e.g. correct drive order).  I am now checking the array's integrity with `/usr/share/mdadm/checkarray /dev/md127`.

I'll report the status after the verification is complete. So far so good:

```

Every 1.0s: cat /proc/mdstat                                                                                                                                                 Fri May 25 02:44:10 2012

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10]
md127 : active raid6 sdf1[6] sdg1[5] sdh1[4] sdb1[3] sdc1[2] sdd1[1] sde1[0]
      9767552000 blocks super 1.2 level 6, 512k chunk, algorithm 2 [7/7] [UUUUUUU]
      [==>..................]  check = 10.2% (199343504/1953510400) finish=372.0min speed=78572K/sec

```

@jgrevich
I did exactly what you did however I don't seem to have any partitions under /dev/md1. Did you run fsck as instructed here? [http://en.wikipedia.org/wiki/Mdadm#Recovering_from_a_loss_of_raid_superblock]("http://en.wikipedia.org/wiki/Mdadm#Recovering_from_a_loss_of_raid_superblock") I recieve an error when trying to run ```
fsck.ext4 /dev/md1
``` saying the filesystem type is incorrect.

---

### Post by jgrevich on 2012-12-22
Hi Jimmah,

Sorry to hear of your troubles.  Are you sure you rebuilt the array using the correct drive order?  It's not usually alphabetical like you would think. I looked in an old syslog or dmesg to get the correct drive order when it was assembled correctly (notice how my order was EDCBHGF, not BCDEFGH).

The filesystem check will fail if it wasn't rebuilt (mdadm --create --assume-clean) in the correct order.  You will need to remove the --assume-clean option if you know that a specific drive is degraded.

Hope that helps.



justin

---

