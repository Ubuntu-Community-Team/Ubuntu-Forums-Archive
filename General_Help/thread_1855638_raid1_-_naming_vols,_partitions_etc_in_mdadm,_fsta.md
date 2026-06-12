---
title: "raid1 - naming vols, partitions etc in mdadm, fstab"
date: 2011-10-06
forum: General Help
---

### Post by canucksailor on 2011-10-06
ubuntu 11.04 server 64bit, asus m/b, sda solid state, sdb 500GiB (no probs), 2 x Seagate Constellation 1Tb as sdc|sdd, corei7, 8 gigs ram, clean install with minimum gnome (see below)

I'm a noobie to software raid (mdadm); cannot get 2 valid raid1 drives to mount from boot (have to use "S" to skip). After boot, cannot mount via "sudo mount -a" - BUT Gnome "Disk Utility" mounts them with no problems, but at /media, not /mnt

```

paul@nelson:~$ sudo mdadm --detail --scan
ARRAY /dev/md/0 metadata=1.2 name=nelson:0 UUID=b351b671:24504147:6d51fab9:5f6606eb
ARRAY /dev/md/1 metadata=1.2 name=nelson:1 UUID=02b57dcd:cf09f2c4:7eeccd39:510df0b1

paul@nelson:~$ cat /etc/fstab
# /etc/fstab: static file system information.
[snip]
# definitions of existing MD arrays
ARRAY /dev/md/1 metadata=1.2 name=nelson:1 UUID=02b57dcd:cf09f2c4:7eeccd39:510df0b1
ARRAY /dev/md/0 metadata=1.2 name=nelson:0 UUID=b351b671:24504147:6d51fab9:5f6606eb

paul@nelson:~$ sudo mount -a
mount: special device UUID=b351b671:24504147:6d51fab9:5f6606eb does not exist
mount: special device UUID=02b57dcd:cf09f2c4:7eeccd39:510df0b1 does not exist

```I *think* it's a problem with naming the raid drives - variously md0, md/0, md_0, md0p1, nelson:0 (nelson is the server name), but as you can see above, using UUID does not force recognition.

I can't find what is ahead of mdadm (ureadahead? something obscure in init.d), because I do have mount points in /mnt:

```
paul@nelson:/mnt$ ls
backup  home  md  nelson:0  nelson:1 
paul@nelson:/mnt/md$ ls
0  1
```but Gnome **after boot**, can (how? why?) mount them in /media:

```
paul@nelson:/mnt$ ls -l
drwx-w--w- 4 paul paul 4096 2011-10-03 09:01 backup
drwxr-xr-x 2 root root 4096 2011-10-01 19:42 cdrom
drwx------ 4 paul paul 4096 2011-10-06 15:21 home
```Can anyone help, please?  I'm sure it's simple, but my brain might have gone into a loop that can't see the obvious.  tnx - paul

---

### Post by blueridgedog on 2011-10-06
You are trying to create two array's?  What partitions are in the array's?  What raid level?

What is the full output of sudo /fdisk -l?

---

### Post by canucksailor on 2011-10-06
mnay tnx yr reply.  sdc and sdd are the two 1TB drives containing the ext4 synched raid1 drives:

```
paul@nelson:/$ sudo fdisk -l
[snip]   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4866    39080960   83  Linux
[snip]   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2040    16384000   82  Linux swap / Solaris
/dev/sdb2            2040        5865    30720000   83  Linux
/dev/sdb3            5865        9690    30720000   83  Linux
/dev/sdb4            9690       60802   410557440   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00078724

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        3188    25600000   fd  Linux raid autodetect
/dev/sdc2            3189        6834    29286495   fd  Linux raid autodetect

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000330f6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        3188    25600000   fd  Linux raid autodetect
/dev/sdd2            3189        6834    29286495   fd  Linux raid autodetect

Disk /dev/md1: 30.0 GB, 29988248576 bytes
2 heads, 4 sectors/track, 7321349 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00039435

    Device Boot      Start         End      Blocks   Id  System
/dev/md1p1               1     7321349    29285394   83  Linux

Disk /dev/md0: 26.2 GB, 26213277696 bytes
255 heads, 63 sectors/track, 3186 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b5ae4

    Device Boot      Start         End      Blocks   Id  System
/dev/md0p1               1        3187    25595904   83  Linux
```

---

### Post by blueridgedog on 2011-10-06
Ok, so you are trying create two raid drives?

What is the output of 


sudo mdadm --detail /dev/md0

and

sudo mdadm --detail /dev/md1

---

### Post by canucksailor on 2011-10-06
tnx -- here it is:

```
paul@nelson:/$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 1.2
  Creation Time : Tue Sep 27 10:44:24 2011
     Raid Level : raid1
     Array Size : 25598904 (24.41 GiB 26.21 GB)
  Used Dev Size : 25598904 (24.41 GiB 26.21 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Thu Oct  6 16:45:25 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : nelson:0  (local to host nelson)
           UUID : b351b671:24504147:6d51fab9:5f6606eb
         Events : 29

    Number   Major   Minor   RaidDevice State
       0       8       33        0      active sync   /dev/sdc1
       1       8       49        1      active sync   /dev/sdd1

paul@nelson:/$ sudo mdadm --detail /dev/md1
/dev/md1:
        Version : 1.2
  Creation Time : Tue Sep 27 12:38:14 2011
     Raid Level : raid1
     Array Size : 29285399 (27.93 GiB 29.99 GB)
  Used Dev Size : 29285399 (27.93 GiB 29.99 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Thu Oct  6 16:07:18 2011
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : nelson:1  (local to host nelson)
           UUID : 02b57dcd:cf09f2c4:7eeccd39:510df0b1
         Events : 33

    Number   Major   Minor   RaidDevice State
       0       8       34        0      active sync   /dev/sdc2
       1       8       50        1      active sync   /dev/sdd2
```

---

### Post by blueridgedog on 2011-10-07
I have asked a few times, but not gotten a direct reply:  You have two array's, so I assume you are trying to make two.

The two array's are md0 and md1.  They each only have one partition in them:

/dev/md1p1               1     7321349    29285394   83  Linux
/dev/md0p1               1        3187    25595904   83  Linux

md0 is made up of /dev/sdc1 and /dev/sdd1.  md1 is made up of /dev/sdc2 and /dev/sdd2.

To have these mount at boot, I would add the partitions, not the devices, to /etc/fstab:


```
/dev/md0p1 /your/mount/point  ext4    errors=remount-ro 0 1
/dev/md1p1 /your/mount/point  ext4    errors=remount-ro 0 1
```

Note that you will need to change the mount point and the type if they are not ext4.  Also note that the mount point must exist.

I would also comment out the other references to the arrays in fstab.

The reason gnome mounts them as it sees the partitions md0p1 and md1p1 and notes that they are not mounted in fstab and mounts them as media.  I can't see anywhere in the snipet of fstab that you posted that the partitions are being mounted.

---

### Post by canucksailor on 2011-10-07
Many tnx - I had a "duh moment" and had copied mdadm -- detail --scan to both mdadm.conf and fstab

You also mention "need to change the mount point and the type if they are not ext4".  I am about to add more raid1 partitions, a primary sd[c,d]3 as ext4 (hopefully no prob), then the last primary sd[c|d]4 as an extended partition for three NTFS logical partitions (for LAN use with Win machines.)

I can create the mount points for md2p1 and md3p[1,2,3], but had trouble (previous attempt prior to complete reinstall) with NTFS and/or ntfs-g3.  You recommended ```
errors=remount-ro
```rather than ```
 rw,auto,user 
```What is best practice for ntfs?  [A little OT for this thread, but I tried fdisk, cfdisk and gparted to make the ntfs partitions and had problems with each of them - mostly with syncing the ntfs which always seemed to want to be bigger than the partition.]

Again, many thanks - you're saving my sanity

---

### Post by blueridgedog on 2011-10-07
> **canucksailor said:**
> I am about to add...three NTFS logical partitions (for LAN use with Win machines.)

If the server is Linux, what value is there in having an NTFS partition type locally to share on the wire?  Linux support for NTFS is poor to fair for reading, and unacceptable for much else.  I would use ext4 for the windows shares, then share them via samba.  Is there a specific reason you want NTFS for the partition type (I am not even certain you can create them and format them in Linux)?  Perhaps there is something that I am missing.  

As a shared drive, the local partition type is almost moot, but needs to be something that the host OS knows how to manage from a user and permission standpoint.  NTFS fails at this as Linux can't run the local file permission model required for local NTFS access control.

Finally, what will control permissions and access?  Is there a windows domain or will permissions and access be done on the Linux server?

---

