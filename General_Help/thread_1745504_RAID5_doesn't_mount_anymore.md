---
title: "RAID5 doesn't mount anymore"
date: 2011-05-01
forum: General Help
---

### Post by tusi on 2011-05-01
Hello guys.

I have a problem with my RAID5 array. And since I am new in  ubuntu I am kind of stuck here.

I have 4 discs in array, all WD20EARS. I am using ubuntu server 10.04.

So I used this command to make partitions.

[FONT="Courier New"]sudo fdisk -H 224 -S 56 /dev/sda[/FONT]

All partitions are primary, type Linux raid autodetect.

[FONT="Courier New"]Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
224 heads, 56 sectors/track, 311465 cylinders
Units = cylinders of 12544 * 512 = 6422528 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x379ece3d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      311465  1953508452   fd  Linux raid autodetect[/FONT]

In next step I created an array with this command.

[FONT="Courier New"]sudo mdadm --create /dev/md0 --level=5 --spare-devices=0 --raid-devices=4 /dev/sda1 /dev/sdb1 /dev/sdc1 /dev/sdd1[/FONT]

Then the detail is saying this:

[FONT="Courier New"]tusi@ubuntu:~$ sudo mdadm --detail --scan /dev/md0
/dev/md0:
        Version : 00.90
  Creation Time : Sun May  1 09:31:56 2011
     Raid Level : raid5
     Array Size : 5860525056 (5589.03 GiB 6001.18 GB)
  Used Dev Size : 1953508352 (1863.01 GiB 2000.39 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun May  1 09:31:56 2011
          State : clean, degraded, recovering
 Active Devices : 3
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 1

         Layout : left-symmetric
     Chunk Size : 64K

 Rebuild Status : 0% complete

           UUID : bab3c10d:eb89ff21:6b97633d:455aabfc
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       4       8       49        3      spare rebuilding   /dev/sdd1[/FONT]

After that, I created filesystem on /dev/md0.

[FONT="Courier New"]sudo mkfs -t ext4 /dev/md0[/FONT]

And mount it and added fstab line:

[FONT="Courier New"]sudo mount /dev/md0 /mnt/storage[/FONT]

[FONT="Courier New"]/dev/md0   /mnt/storage   ext4   defaults   0   0[/FONT]

And it was working for 2 days, they system gave me some fs error and it hanged and since then, I can not mount it anymore.
The command:  [FONT="Courier New"]sudo mdadm --detail --scan /dev/md0[/FONT] is still working. Result is up. But I can not mount it.

[FONT="Courier New"]tusi@ubuntu:~$ sudo mount -t ext4 /dev/md0 /mnt/storage1
mount: wrong fs type, bad option, bad superblock on /dev/md0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so[/FONT]

When I use fsck, it gives me a lot of errors.

[FONT="Courier New"]sudo fsck -t ext4 -y /dev/md0
And how it ends with system abort:
Illegal block #5 (3296069779) in inode 115971.  CLEARED.
Illegal block #8 (3273687952) in inode 115971.  CLEARED.
Illegal block #9 (3285732525) in inode 115971.  CLEARED.
Illegal block #11 (2310363380) in inode 115971.  CLEARED.
Illegal indirect block (3503930346) in inode 115971.  CLEARED.
Illegal double indirect block (3479795423) in inode 115971.  CLEARED.
Illegal indirect block (4156467269) in inode 115971.  CLEARED.
Illegal indirect block (2298545117) in inode 115971.  CLEARED.
Inode 115971 is too big.  Truncate? yes

Block #7344254 (1086387853) causes directory to be too big.  CLEARED.
Too many illegal blocks in inode 115971.
Clear inode? yes

Inode 116483 has compression flag set on filesystem without compression support.  Clear? yes

Inode 116483 has a bad extended attribute block 1356032982.  Clear? yes

Inode 116483 has illegal block(s).  Clear? yes

Illegal block #0 (2096955614) in inode 116483.  CLEARED.
Illegal block #3 (2343046912) in inode 116483.  CLEARED.
Illegal block #5 (3296069779) in inode 116483.  CLEARED.
Illegal block #8 (3273687952) in inode 116483.  CLEARED.
Illegal block #9 (3285732525) in inode 116483.  CLEARED.
Illegal block #11 (2310363380) in inode 116483.  CLEARED.
Illegal indirect block (3503930346) in inode 116483.  CLEARED.
Illegal double indirect block (3479795423) in inode 116483.  CLEARED.
Inode 116483 is too big.  Truncate? yes

Block #7344255 (306684) causes directory to be too big.  CLEARED.
Error storing directory block information (inode=116483, block=0, num=2969397): Memory allocation failed
e2fsck: aborted[/FONT]

So the question is, how can I restore data and make RAID working again.
Thank you guys!

---

### Post by epud on 2011-05-01
My motherboard controls my RAID I had a very similar problem. My solution was here: [https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/770600](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/770600)

Not sure if this will work for you but might be worth giving it a try?

---

### Post by a2j on 2011-05-01
tusi
what does
```
mdadm --detail /dev/md0
```
say right now?

any of the drives have bad sectors?

I had an issue (sectors) with 1 WD15EARS in software RAID10, 3 months after I bought it.

---

### Post by tusi on 2011-05-01
```
/dev/md0:
        Version : 00.90
  Creation Time : Sun May  1 10:56:40 2011
     Raid Level : raid5
     Array Size : 5860525056 (5589.03 GiB 6001.18 GB)
  Used Dev Size : 1953508352 (1863.01 GiB 2000.39 GB)
   Raid Devices : 4
  Total Devices : 4
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Sun May  1 10:56:40 2011
          State : clean
 Active Devices : 4
Working Devices : 4
 Failed Devices : 0
  Spare Devices : 0

         Layout : left-symmetric
     Chunk Size : 64K

           UUID : 4770a6e2:a2e1768a:d86bc202:1ead42a9
         Events : 0.1

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
       2       8       33        2      active sync   /dev/sdc1
       3       8       49        3      active sync   /dev/sdd1

```

All disk are new. How can I check individual disk for bad sectors if it's in an array, partitioned as linux raid?

---

### Post by tusi on 2011-05-01
I also tried to mount the with live distribution. All is the same, except fsck gives this in the end.

```
Warning... fsck.ext4 for device /dev/md0 exited with signal 9.
```

---

### Post by a2j on 2011-05-01
your array looks fine to me... 
but, if you're new to Linux (ubuntu), I'd use [webmin]("http://www.webmin.com/"). Download debian package. This can help you a lot. Setting arrays, checking disks for error, etc...

PS: your OS is also on some raid array?

---

### Post by tusi on 2011-05-02
Looks fine to me too, just that it doesn't want to mount again.

I installed Webmin. Looks cool, just it doesn't help in this situation.

My OS is on USB key, running on:
Kernel and CPU:	Linux 2.6.32-28-server on x86_64
Processor information:	Intel(R) Atom(TM) CPU D510 @ 1.66GHz, 4 cores

---

### Post by a2j on 2011-05-02
did you do any changes before it failed to mount?
is it a server? or you shut it down daily?
make sure all the drives are healthy. check them one at the time if necessary. 

that is where I'd start.

---

