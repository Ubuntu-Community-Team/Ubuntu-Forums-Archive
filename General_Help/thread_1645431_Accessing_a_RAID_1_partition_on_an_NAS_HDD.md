---
title: "Accessing a RAID 1 partition on an NAS HDD"
date: 2010-12-14
forum: General Help
---

### Post by DeanB on 2010-12-14
I've got a Western Digital My Book World 2nd ed. NAS drive.  It has two 2TB HDDs set to RAID 1, so it backs itself up.  For some reason I can no longer access its data.  Western Digital has helped me try to access the data by instructing me to boot my PC with Ubuntu (first time Linux experience), attach either of my troubled drives via a drive adapter setup, and mount their partitions with the following instructions:

sudo mount -t ext3 -o ro /dev/sdd4 /mnt  (sdd4 was the name given the data partition by the system)

I've been able to mount two of the four partitions, but not the valuable data one.  When trying to mount the data partition I get the following error message:

mount: wrong fs type, bad option, bad superblock on /dev/sdd4, missing  codepage or helper program, or other error. In some cases useful info is  found in syslog - try dmesg | tail or so

I'm not a programmer, and not a Linux expert, but when I type dmesg I find an error message pertaining to my data partition saying: 

error: can't find ext3 filesystem on dev sdd4

So I assume somethings wrong with the ext3 filesystem.  Is there anyone who's familiar with this sort of thing who would know how or if it's possible to overcome this error and access the data?

Thank you

---

### Post by SaturnusDJ on 2010-12-15
Maybe the 'e2fsck' of [E2fsprogs]("http://en.wikipedia.org/wiki/E2fsprogs") helps. Using the others (except dumpe2fs) might be risky.

What happens if you don't use the 'ext3' format in the mount command?

---

### Post by DeanB on 2010-12-16
Thanks for your response.  I'll have to look into your e2fsk suggestion (I'm wholly unfamiliar with the Linux world).  I tried the command without ext3 in the command line and got a lot of "advice" from the system telling me  "that one does not really mount a device, one mounts a filesystem (of the given type) found on the device."  I've tried mounting with ext2, ext3, and ext4, all to no avail.  I believe it's supposed to be ext3, but for some reason it cannot be mounted.  It appears that something's corrupted the drive, preventing me in mounting to the filesystem.  Do you think your e2fsk is an avenue to addressing this?

Thanks

---

### Post by SaturnusDJ on 2010-12-16
I think you won't have much choice.

But before you do that: what kind of RAID setup do you have? Hardware RAID? Are you sure it is ext3 and not something else? Try if GParted or fdisk can recognise any partition.

---

### Post by rubylaser on 2010-12-16
Dean can you paste in the output of this?

```
fdisk -l
```

With the partition unmounted, you could try this to run a filesystem check...
```
fsck.ext3 /dev/sda3
```  Or, whatever partition numbers show up in fdisk -l

Once, you provided us with those details, it should be easier to help you.

---

### Post by dmitryilyin on 2010-12-16
Use disktype first

install disktype:
aptitude install disktype

use disktype on your disk:
disktype /dev/sda

it will print what partitions and file systems are there

Then find what partition you are looking for and what filesystem it has and mount it

---

### Post by SaturnusDJ on 2010-12-16
I just thought of something. It looks like your WD NAS is running some kind of linux version. This could mean the RAID1 array is mdadm based. Mdadm manages RAID.
This brings the conclusion that you try to mount a 'linux_raid_member' filesystem. That's why you get the error.

[http://en.wikipedia.org/wiki/Western_Digital_My_Book#Internals](http://en.wikipedia.org/wiki/Western_Digital_My_Book#Internals) confirms this. The page also lists some commands to mount the disk(s). You need to use the first set of commands which are these:
```

modprobe md
mknod /dev/md4 b 9 4
apt-get install mdadm
mdadm&#8212;assemble /dev/md4 /dev/sdb4
mkdir /media/xyz
mount /dev/md4 /media/xyz
chmod -R 777 /media/xyz

```
Modprobe connects/refreshes your HDD's or so, if they aren't already.
I don't know mknod. It looks like it does something to make assembling in mdadm possible. (Maybe undo a small modification WD added, which also blocked the mount command from seeing the drives are linux_raid_members)
The following two commands install mdadm and assambles a degraded RAID1 array. The rest is mounting, see what you need of that, I think chmoding isn't really needed.

---

### Post by rubylaser on 2010-12-16
You don't want to just try to force an mdadm array together without knowing first that it's an mdadm array.  Installing mdadm won't hurt, but you'll want to verify first before putting it together.  Just run this on each partition.  To do this, just 

```
sudo -i
```

```
apt-get install mdadm
```
```
mdadm --examine /dev/sdd1
```

If it's an mdadm array, you'll see info like this (much shorter though, because it's a two disk array.)
```
root@fileserver:~# mdadm --examine /dev/sdd1
/dev/sdd1:
          Magic : a92b4efc
        Version : 0.90.00
           UUID : d4e58776:640274d8:e368bf24:bd0fce41
  Creation Time : Sun Aug  1 16:26:04 2010
     Raid Level : raid6
  Used Dev Size : 976759808 (931.51 GiB 1000.20 GB)
     Array Size : 5860558848 (5589.06 GiB 6001.21 GB)
   Raid Devices : 8
  Total Devices : 8
Preferred Minor : 0

    Update Time : Thu Dec 16 06:03:33 2010
          State : clean
 Active Devices : 8
Working Devices : 8
 Failed Devices : 0
  Spare Devices : 0
       Checksum : 562c5566 - correct
         Events : 16736

         Layout : left-symmetric
     Chunk Size : 512K

      Number   Major   Minor   RaidDevice State
this     0       8       17        0      active sync   /dev/sdb1

   0     0       8       17        0      active sync   /dev/sdb1
   1     1       8       65        1      active sync   /dev/sde1
   2     2       8       49        2      active sync   /dev/sdd1
   3     3       8       33        3      active sync   /dev/sdc1
   4     4       8       97        4      active sync   /dev/sdg1
   5     5       8      129        5      active sync   /dev/sdi1
   6     6       8      113        6      active sync   /dev/sdh1
   7     7       8       81        7      active sync   /dev/sdf1

```

Again, if we could see the disk partitions, it would remove the guesswork.

---

### Post by DeanB on 2010-12-16
Ok everyone, thanks for your assistance.  Here's what I've uncovered:

**1.  Installing mdadm gives me problems.  I get the following message with errors at the end (E:)- **

ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# apt-get install mdadm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  postfix
Suggested packages:
  procmail postfix-mysql postfix-pgsql postfix-ldap postfix-pcre sasl2-bin
  resolvconf postfix-cdb
The following NEW packages will be installed:
  mdadm postfix
0 upgraded, 2 newly installed, 0 to remove and 199 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/
root@ubuntu:~# 

I also tried installing via the Synaptic Package Manager which gave the same errors.
[B]
2. Here's what I get with the fdisk -l command (I'm pasting only the disk in question)-[/B]

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001cf00

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               5         248     1959930   fd  Linux raid autodetect
/dev/sda2             249         280      257040   fd  Linux raid autodetect
/dev/sda3             281         403      987997+  fd  Linux raid autodetect
/dev/sda4             404      243201  1950274935   fd  Linux raid autodetect

**3. Here's what I get with disktype-**

ubuntu@ubuntu:~$ sudo disktype /dev/sda

--- /dev/sda
Block device, size 1.819 TiB (2000398934016 bytes)
DOS/MBR partition map
Partition 1: 1.869 GiB (2006968320 bytes, 3919860 sectors from 64260)
  Type 0xFD (Linux raid autodetect)
  Ext3 file system
    UUID 8E051437-F55B-490C-9900-F950A7290077 (DCE, v4)
    Volume size 1.869 GiB (2006843392 bytes, 489952 blocks of 4 KiB)
  Linux RAID disk, version 0.90.0
    RAID1 set using 2 regular -1 spare disks
    RAID set UUID 75E73E4F-76BA-53CD-BBBC-7735CCC6EBE2 (DCE, v5)
Partition 2: 251.0 MiB (263208960 bytes, 514080 sectors from 3984120)
  Type 0xFD (Linux raid autodetect)
  Linux RAID disk, version 0.90.0
    RAID1 set using 2 regular 0 spare disks
    RAID set UUID AFFC6FDB-7E21-15CA-A056-D66509A90556 (DCE, v1)
  Linux swap, version 2, subversion 1, 4 KiB pages, little-endian
    Swap size 250.9 MiB (263118848 bytes, 64238 pages of 4 KiB)
Partition 3: 964.8 MiB (1011709440 bytes, 1975995 sectors from 4498200)
  Type 0xFD (Linux raid autodetect)
  Ext3 file system
    UUID AB81A4C6-60DB-4015-BD36-85F83C6B0ABC (DCE, v4)
    Volume size 964.8 MiB (1011613696 bytes, 246976 blocks of 4 KiB)
  Linux RAID disk, version 0.90.0
    RAID1 set using 2 regular -1 spare disks
    RAID set UUID E6A27133-9CAE-AC55-B4FC-BA072DDDB192 (DCE, v10)
Partition 4: 1.816 TiB (1997081533440 bytes, 3900549870 sectors from 6474195)
  Type 0xFD (Linux raid autodetect)
  Linux RAID disk, version 0.90.0
    RAID1 set using 2 regular -1 spare disks
    RAID set UUID 38ECA297-F2A0-F19F-5FA2-DEAB46C142F3 (NCS)
  XFS file system, version 4
    Volume name ""
    UUID B92F7337-EB45-44C4-82DD-38D77605D505 (DCE, v4)
    Volume size 1.816 TiB (1996682428416 bytes, 487471296 blocks of 4 KiB)


Thank you!

---

### Post by DeanB on 2010-12-16
Ok, some very good news.  With your help in gathering info on my drive's partitions, I noted that the data partition said its filesystem is an XFS file system, version 4.  On a hunch, I took the original mount command from my first message and substituted ext3 with xfs.

[B]sudo mount -t ext3 -o ro /dev/sdd4 /mnt

[/B]changed to[B]

sudo mount -t xfs -o ro /dev/sda4 /mnt[/B]  (note that the partition name was also changed)

The modified command mounted the partition successfully, and I now have access to all of my data.  I'm currently transferring everything to my new replacement drive.

I still don't know what happened in the first place that corrupted the drive, but I'm ecstatic that I'm not shelling out thousands of dollars to retrieve my data.

Thank you very much for all of your help.

Dean

---

### Post by rubylaser on 2010-12-17
Glad to hear you got your data back.  That feeling of having lost everything is not a good one :)

---

