---
title: "FSTAB Timeout"
date: 2010-02-21
forum: General Help
---

### Post by klyndt on 2010-02-21
I woke up this morning to a non-booting 9.10 computer. After my grub screen disappears, I get the familiar Ubuntu b/w logo in the center of my screen. My hard drive cranks for an abnormally long time and then I get the following error:
One or more mounts listed in /etc/fstab cannot be mounted. /home:UUID=(long UUID)

I booted into a live CD and opened up GPARTED and my sdb4 (my /home location) partition shows up. I do a check on it and it _seems_ ok.

I opened the Palimpsest Disk Utility to see what it said and it shows sdb4 as Unknown or Unused.  I can not mount this drive using GUI methods.

I did some research on the forums looking to recover lost partitions. here is the output from fsck
```
ubuntu@ubuntu:/$ sudo fsck /dev/sdb4
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
/dev/sdb4: clean, 44145/4571136 files, 1879626/9140985 blocks

```
and the abbreviated output from fdisk -l
```
Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x59d03d7e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        8511    68364576    7  HPFS/NTFS
/dev/sdb2            8512        9786    10241437+  83  Linux
/dev/sdb3            9787       10041     2048287+  82  Linux swap / Solaris
/dev/sdb4           10042       14593    36563940   83  Linux

```
This seems ok too.
My next step was to try testdisk.  When I ran it, I was able to navigate this partition and apparently see all my files.
I then tried to mount the partition manually.
```
sudo mount -t ext3 /dev/sdb4 /mnt
```
That also worked.
It seems to me that I practically have this thing where I need it without too many worries.  My question is: What is the next step to get this back booting again? I'm afraid of rewriting the partitions in testdisk until I get some feedback on whether this will really solve my problem. Maybe the partition isn't the problem? Is it something else and I've been going down the wrong path?

Thanks for any help, Klyndt

---

### Post by klyndt on 2010-02-21
I followed the steps on the testdisk site and rewrote my partition table. Nothing changed.  Now I'm at a loss for what is wrong.  Ubuntu still doesn't boot, the disk utility still says the partition is Unrecognizable and GParted still says this is a EXT3 partition.

Does anyone have any ideas on what to try next?

Thanks,
Klyndt

---

### Post by b0b138 on 2010-02-21
From the cd run sudo blkid and double check the uuid it lists for that partition against what is listed in fstab.  If its the same, edit fstab and remove the UUID=blahblahblah and put in /dev/sdb4 instead

---

### Post by klyndt on 2010-02-21
blkid doesn't list the partition.

```
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="AAB8DA98B8DA61FD" LABEL="BACKUP" TYPE="ntfs" 
/dev/sdb1: UUID="BEDC9B26DC9AD84B" LABEL="Boot" TYPE="ntfs" 
/dev/sdb2: UUID="067e1f54-c85c-4b8a-ab01-9b07a5a20fc8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb3: UUID="0da9844d-2136-4569-a1b6-d08824a78040" TYPE="swap" 
/dev/sdc1: UUID="B204BC5904BC21F1" LABEL="Media" TYPE="ntfs" 

```

I have double checked the UUIDs and the one it complains about at boot-up is the one connected to sdb4 and is the one in fstab.

Klyndt

---

### Post by klyndt on 2010-02-24
I mounted the drive and retried the blkid and it still doesn't show up. What does that mean?

Klyndt

---

