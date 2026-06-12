---
title: "XFS partition shrinks on reboot"
date: 2011-01-22
forum: General Help
---

### Post by mydigitalvoid on 2011-01-22
Hello,

I created a large partition using parted (~6TB) and XFS.  Everything seemed to be fine until I rebooted the system and now I seemed to have lost that partition.  The details are:

```
media@media:~$ uname -a
Linux media 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux
```

Notice that sdb1 is much smaller than sdb?

```
media@media:~$ cat /proc/partitions 
major minor  #blocks  name

   8        0  124917760 sda
   8        1       1024 sda1
   8        2  119797760 sda2
   8        3    5116928 sda3
   8       16 5851043840 sdb
   8       17 1556076510 sdb1
```

```
media@media:~$ sudo mount -t xfs /dev/sdb1 /share
mount: /dev/sdb1: can't read superblock
```

```
[  152.277640] I/O error in filesystem ("sdb1") meta-data dev sdb1 block 0x2b97fafb7       ("xfs_read_buf") error 5 buf count 512
[  152.277645] XFS: size check 2 failed
[  244.474876] attempt to access beyond end of device
[  244.474883] sdb1: rw=0, want=11702087608, limit=3112153021
[  244.474890] I/O error in filesystem ("sdb1") meta-data dev sdb1 block 0x2b97fafb7       ("xfs_read_buf") error 5 buf count 512
[  244.474896] XFS: size check 2 failed
[ 5225.078715] attempt to access beyond end of device
[ 5225.078721] sdb1: rw=0, want=11702087608, limit=3112153021
[ 5225.078728] I/O error in filesystem ("sdb1") meta-data dev sdb1 block 0x2b97fafb7       ("xfs_read_buf") error 5 buf count 512
[ 5225.078734] XFS: size check 2 failed
```

```
media@media:~$ grep CONFIG_EFI_PARTITION /boot/config-`uname -r`
CONFIG_EFI_PARTITION=y
```

```
media@media:~$ sudo parted /dev/sdb print
Model: Adaptec Data (scsi)
Disk /dev/sdb: 5991GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  5991GB  5991GB  xfs          xfs
```

I've dug around and found there were some issues with older versions of Ubuntu w/ parted but these seem to have been resolved.  The problem I think has to do with the partition table only seeing part of the partition and thus causing "size check 2".  I'm really not sure if this is recoverable but if it is I'd like to recover it :)  Please let me know if there is a way to fix this.

Thank you so much!

-Dustin

---

### Post by srs5694 on 2011-01-22
Your parted output suggests that the partition table is fine. If you want a second opinion on that score, you could download and install my GPT fdisk (gdisk) program from [its Sourceforge download page.](http://sourceforge.net/projects/gptfdisk/files/) (Don't use the version in the Ubuntu repositories; it's hopelessly out of date.) Run the program and use the "v" option to verify the disk's integrity:

```

$ **sudo gdisk /dev/sdb**
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): **v**
No problems found. 4670 free sectors (2.3 MiB) available in 1
segments, the largest of which is 4670 (2.3 MiB) in size.

Command (? for help): **q**

```

This shows that the GPT data on my example disk are intact and self-consistent. If there were problems (overlapping partitions, misplaced backup data, etc.), the "v" command would report them. Some problems will also generate warnings when you first start the program. You can also use the "p" command to view the partition table, verifying that /dev/sdb1 is (or is not) the proper size.

Right now, it looks to me like your problem is a kernel bug. I'm not aware of such a bug that affects GPT on large disks, but it could be I just don't know about the issue. You could try Googling on it, or just blindly upgrade to the latest kernel from [http://www.kernel.org](http://www.kernel.org) and hope that it fixes it. It's also conceivable that the issue is in the drivers for your RAID controller card, although if that were the case I'd expect to see the entire array (/dev/sdb) shrinking, not just one partition.

---

### Post by mydigitalvoid on 2011-01-22
Thank you so much for the response!

This is what I got:

```
media@media:~$ sudo gdisk /dev/sdb
GPT fdisk (gdisk) version 0.6.14

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: present

Found valid MBR and GPT. Which do you want to use?
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: 2
Using GPT and creating fresh protective MBR.

Command (? for help): v

Caution: Partition 1 doesn't begin on a 8-sector boundary. This may
result in degraded performance on some modern (2009 and later) hard disks.
No problems found. 0 free sectors (0 bytes) available in 0
segments, the largest of which is 0 (0 bytes) in size.

Command (? for help): i
Using 1
Partition GUID code: EBD0A0A2-B9E5-4433-87C0-68B6B72699C7 (Linux/Windows data)
Partition unique GUID: 9EED4793-9699-4162-9D77-7C8B024CBBE4
First sector: 34 (at 17.0 KiB)
Last sector: 11702087646 (at 5.4 TiB)
Partition size: 11702087613 sectors (5.4 TiB)
Attribute flags: 0000000000000000
Partition name: xfs
```


The Raid card has the latest firmware.  I can try a new kernel, but I wasn't able to find any bug references.  Maybe I'll blow it away and switch it to ext3 but I wanted to at least back the data up off of it first :-/

---

### Post by mydigitalvoid on 2011-01-24
Well, still can't figure out what's wrong, but I found a way to at least correct it.  Since the partition tables aren't being destroyed, running a partprobe on the partition corrects /proc/partitions and then mounting it works fine.

I'm still at a loss as to what's causing it though.  For kicks, I destroyed and recreated the partition table using parted and then rebooted the box without putting a filesystem on it and when it came back up it still only displayed about 1.5TB or storage.  So, the problem isn't specific to xfs.

---

### Post by srs5694 on 2011-01-24
Sorry, I seem to have missed your response from yesterday. It looks like your partition table is corrupted -- you've got GPT data, but also MBR data that doesn't include a GPT protective (type-0xEE) partition. This probably accounts for the problem. A literal reading of the GPT specification says that in this case, the computer should use the MBR data. Chances are Linux is doing this and so is showing you a ~1.5 GiB MBR partition. Some partitioning tools, though, apparently including the version of parted you're using, use the GPT data in this situation. GPT fdisk, though, flags the problem and gives you a choice of which to use.

Since you've got a ~6 TiB disk, MBR is inadequate, and I'm guessing that your GPT data are correct. To fix the problem, do this:


[list=1]
[*]Launch gdisk on the disk, as you did in the sample output you posted yesterday.
[*]When prompted, opt to use the GPT data, as you did in the sample output you posted yesterday.
[*]Type "p" to view the partition table and verify that it's correct. If it's not, type "q" to quit without saving. If it looks right, proceed (but see my comments below)....
[*]Type "w" to save the changes (namely, the new protective MBR that gdisk automatically created when you told it to use the GPT data).
[/list]


That's it (but see below). I recommend rebooting at this point to be sure the problem is gone.

You should be aware that many types of hardware RAID array suffer from degraded performance when partitions are not properly aligned. For such arrays, proper alignment typically means alignment on 16 KiB, 32 KiB, 64 KiB, 128 KiB, or 256 KiB boundaries, but the details depend on the RAID controller's configuration. Modern disk utilities align on 1 MiB boundaries by default, and this is almost always safe. Your disk's partition is not properly aligned, so you're likely to see performance degradation of 5% to 30%.

To fix this problem, you'll have to either move/resize the partition so that it starts on a proper sector value or delete the partition and re-create it. (The latter will of course destroy all your data, and the former poses a risk of doing so if you encounter a problem mid-resize.) You can use gdisk to do the deletion and re-creation, but not the resizing. If you delete and re-create the partition in gdisk, specify a starting sector of 2048 and you'll be fine. (The ending sector value isn't an issue.) How to do this in parted or GParted depends on the version of the program you're using. Setting the units to sectors and specifying a start point of 2048 should work in parted, though.

---

### Post by mydigitalvoid on 2011-01-24
Ah wow, okay, thanks for the information.  I did the following when making the partition:

mkpart ext4 0 -1s

What your saying to do is:

mkpart ext4 2048s -1s

I'm going to read up on your gdisk program and try to use that to repartition the raid.

I will try that tonight and let you know what happens.  Thank you so much for your help in this matter.  Thank you so much again!

---

### Post by mydigitalvoid on 2011-01-24
That did the trick!  I just created a new partition with a starting sector of 2048, put ext4 on it, then used gdisk to create the protective MBR and rebooted.  When it came up /proc/partitions was correct :)  Thank you kind sir!

---

### Post by srs5694 on 2011-01-24
I'm glad that worked for you!

---

