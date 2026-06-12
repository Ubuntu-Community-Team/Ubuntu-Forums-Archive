---
title: "&quot;can't find [HDD] in /etc/fstab or /etc/mtab&quot;"
date: 2011-11-03
forum: General Help
---

### Post by stg on 2011-11-03
Was fooling around with gparted and clonezilla

Now I can not mount one of my drives. The BIOS sees it fine.  It passes all tests on the disk manufacturer's live diagnostic CD.  If I ls /dev/sd* it shows up as /dev/sdb but when I try to mount it says "can't find /dev/sdb in /etc/fstab or /etc/mtab"

??

---

### Post by WorMzy on 2011-11-03
Two things:
1) You can't mount a harddrive (except in rare cases, where the drive is basically just one big partition)

2) You need to specify a mount point if you're using the mount command

e.g.

```
sudo mount /dev/sdb1 /mnt
```

Now, if you don't have any partitions (e.g. sdb1, sdb2, sdb5, etc) on the drive, you'll need to make one (unless your drive is one of the rare cases I mentioned above).

Hpefully this points you in the right direction and you can sort your self out from there, but if you're still struggling to understand why you can't mount it, post the output of:

```
sudo parted -l
```

here.

---

### Post by stg on 2011-11-03
Thanks!

here are the outputs of your suggestions

stg@gigtower:~$ sudo mount /dev/sdb /mnt
[sudo] password for stg: 
mount: you must specify the filesystem type
stg@gigtower:~$ sudo mount /dev/sdb1 /mnt
mount: special device /dev/sdb1 does not exist
stg@gigtower:~$ sudo parted -l
Model: ATA IBM-DTTA-350840 (scsi)
Disk /dev/sda: 8455MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
 1      32.3kB  8044MB  8044MB  primary   ext3         boot 
 2      8044MB  8447MB  403MB   extended                    
 5      8044MB  8447MB  403MB   logical   linux-swap        


Error: /dev/sdb: unrecognised disk label                                  

stg@gigtower:~$

---

### Post by WorMzy on 2011-11-03
> Error: /dev/sdb: unrecognised disk label 

Hm. I've never gotten that error.

Does the disk show up in gparted at all? Can you take a screenshot of it if it does, and post it here?

---

### Post by stg on 2011-11-03
Yes it show's up, can't get the screenshot to work but I believe the operative information is

unallocated

invalid partition table - recursive partition on /dev/sda.

all I did was try to pull an image saved on it on to another drive with clonezilla, is there any way to restore this partition table??

---

### Post by WorMzy on 2011-11-03
On sda? Was that a typo?

If you have/had any important data on the drive, I recommend that you use something like [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to recover what you can. Otherwise, just create a new partition table on the disk (select sdb, then go to Device -> Create Partition Table).

After you've created a new partition table, make a partition. Ext4 is a good choice if you're only going to use the partition from Linux.

---

### Post by stg on 2011-11-04
solved

gpart -w

restore partition table

---

