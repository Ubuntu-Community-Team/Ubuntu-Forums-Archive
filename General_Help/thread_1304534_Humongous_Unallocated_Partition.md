---
title: "Humongous Unallocated Partition"
date: 2009-10-29
forum: General Help
---

### Post by Joseph Schwenker on 2009-10-29
Hey, everyone!  I have a 40 GB IDE hard drive that I have been wanting to use as a backup for a while.  However, whenever I try to mount the drive from the "Computer" window, it tells me that it can't mount the drive.  I went into Gparted today, and saw that 38.16 GB of the drive was ext3, and there was a yellow triangle with an exclamation mark in it next to the filesystem name.  I went into the information box, and it said, ```
Warning: 32label: No such file or directory while trying to open /dev/sdb1  Couldn't find valid filesystem superblock.
```

I had formatted this drive in Gparted, and was about to repartition it, when I noticed an interesting unallocated space.  Holy hard drive space!  There was a 2048 TERABYTE unallocated space on my IDE hard drive!  Wow, I wonder how much data you could pack on there?  
So, I want to be able to read and write to that drive, but I am not sure what to do about the humongous unallocated space.  There are no operations available for it.  What should I do?  Thanks!

---

### Post by ColdFFF on 2009-10-29
I think the drive itself is failing.

Even if there were operations available for this unallocated space, I very much doubt they will work.

---

### Post by Joseph Schwenker on 2009-10-29
> **ColdFFF said:**
> I think the drive itself is failing.

Even if there were operations available for this unallocated space, I very much doubt they will work.

So there is no way to use this drive as a backup?

---

### Post by coetzewc on 2009-10-29
typically /dev/sdb1 is an external usb drive my thinking is that it could be your drive enclosure reporting a bad drive config?

---

### Post by ColdFFF on 2009-10-29
Note that I am most definately not an expert with regards to this.

I would _assume_ that because the drive was not mounting correctly before, there was some kind of filesystem issue, and the drive has magically grew to exponential proportions that it is going to be unusable.

Perhaps there are tools available to test/repair such a drive, but until then I personally wouldn't use it for backup or otherwise.

---

### Post by alphaniner on 2009-10-29
> So there is no way to use this drive as a backup? 

You do not have 2048TB of unused space.  You have a bad drive, or a bad IDE cable, or a bad IDE controller.  Download some diagnostic tools from the manufacturer of your HDD.

> **coetzewc said:**
> typically /dev/sdb1 is an external usb drive...

No.

---

### Post by Joseph Schwenker on 2009-10-29
> **alphaniner said:**
> You do not have 2048TB of unused space.  

Yes, I realized that.  :p

---

### Post by Joseph Schwenker on 2009-10-29
Hmm, my manufacturer (Maxtor) has now merged with Seagate, and I have no idea of where to find diagnostic tools.  It is rather old, so I think that I'll just put my OTHER 40 GB hard drive into my machine!  :D

---

### Post by alphaniner on 2009-10-29
[SeaTools]("http://www.seagate.com/www/en-us/support/downloads/seatools") if you want to try it out.  I recommend the bootable SeaTools for DOS.

---

### Post by coetzewc on 2009-10-29
typically /dev/sdb1 is an external usb drive my thinking is that it could be your drive enclosure reporting a bad drive config?

---

### Post by coetzewc on 2009-10-29
sorry guys my clicking is freeking out this thread can the moderator please remove my post

---

### Post by Joseph Schwenker on 2009-10-29
GAAH!!!  I just put in my OTHER 40 GB hard drive, and it mounted successfully the first time.  I then opened Gparted, and clicked unmount (so I could partition it), and gparted unmounts it, then freezed with the stupid progress bar bouncing back and forth like a rubber ball.  I closed out Gparted, and I couldn't mount the drive.  I restarted my computer, and I can no longer mount the drive.  Gparted has it coming up as 45.25 GB (the drive is only 40 GB).  ARGH!!!  What do I do?  Could someone explain those "SeaTools" that were linked to?

---

### Post by alphaniner on 2009-10-29
SeaTools is just a program that checks the drive for errors.  Primarily SMART errors and bad sectors.  If you are having problems with multiple drives, I would do some more troubleshooting first.  It may just be a gparted bug.

What is the output of

```
sudo fdisk -l
```

---

### Post by Joseph Schwenker on 2009-10-29
> **coetzewc said:**
> typically /dev/sdb1 is an external usb drive my thinking is that it could be your drive enclosure reporting a bad drive config?

No, the drive is an internal IDE.

---

### Post by Joseph Schwenker on 2009-10-29
> **alphaniner said:**
> SeaTools is just a program that checks the drive for errors.  Primarily SMART errors and bad sectors.  If you are having problems with multiple drives, I would do some more troubleshooting first.  It may just be a gparted bug.

What is the output of

```
sudo fdisk -l
```

```
fdisk: invalid option -- '1'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

```

---

### Post by alphaniner on 2009-10-29
```
sudo fdisk -**l**
```
(lowercase L)

Speaking of 'L' it's lunchtime for me.  I will check back when I return.

---

### Post by Joseph Schwenker on 2009-10-29
> **alphaniner said:**
> ```
sudo fdisk -**l**
```
(lowercase L)

Speaking of 'L' it's lunchtime for me.  I will check back when I return.

Oh, sorry!  Should have copied and pasted.  My output is:

```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23570   189325993+  83  Linux
/dev/sda2           23571       24321     6032407+   5  Extended
/dev/sda5           23571       24321     6032376   82  Linux swap / Solaris

Disk /dev/sdb: 48.5 GB, 48589934592 bytes
255 heads, 63 sectors/track, 5907 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb1aa9c7

Disk /dev/sdb doesn't contain a valid partition table

```

Enjoy your lunch!

---

### Post by ezsit on 2009-10-29
Instead of relying on Gparted, try cfdisk instead. cfdisk is a command line tool to partition drives that is far easier to use than fdisk. cfdisk does not format the drive, however, you will need to set the drive type correctly (type 82 for a linux swap and type 83 for a linux filesystem). The way to start cfdisk is passing the proper device name without the partition number. If the drive has a swap partition, you should disable swap before proceeding to cfdisk, so:

sudo swapoff -a

then:

sudo cfdisk /dev/sdb

Remember to save your changes before quitting cfdisk or else nothing gets done.

After using cfdisk, you will need to format the drive with the mkfs command and depending on your filesystem preference, the mkfs command would look like this:

sudo mkfs.ext3 /dev/sdb1

---

### Post by alphaniner on 2009-10-29
```
Disk /dev/sdb: 48.5 GB, 48589934592 bytes
255 heads, 63 sectors/track, 5907 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb1aa9c7

Disk /dev/sdb doesn't contain a valid partition table
```

This means that the drive is not partitioned, or the partition table has become corrupted.

I second ezsit's advice to use **cfdisk**, except there is no reason to use **sudo swapoff -a** (because there is no swap on sdb).  After partitioning and formatting, mount the drive.  You should be able to mount it through Nautilus, but if you want to use the terminal do the following:

You will need an empty directory, so for example use

```
sudo mkdir /media/sdb1
```

then mount to that directory with

```
sudo mount /dev/sdb1 /media/sdb1
```

Then take ownership with

```
sudo chown $USER\: /media/sdb1
```

you should now be able to write to the drive.

Write some data then restart.  Remount using Nautilus or the **mount** command I mentioned.  If you don't get any errors and you can see your data, your drive is probably fine.

---

### Post by Joseph Schwenker on 2009-10-29
AAAAAAAAAAAAHHHHHHHHH!!!  This is too confusing!  You are talking about commands like there are as common as air!  Could you please explain to me how to do what ezsit told me to do?  It didn't make much sense.  I can't figure out how to use the cfdisk.  Oh, and I put my original 40 GB hard drive back in.  It is still showing up with a humongous size, this time 6144.10 Terabytes unallocated.  My output for sudo fdisk -l this time is ```
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedaaedaa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23570   189325993+  83  Linux
/dev/sda2           23571       24321     6032407+   5  Extended
/dev/sda5           23571       24321     6032376   82  Linux swap / Solaris

Disk /dev/sdb: -1834425450 MB, 6755509142683648 bytes
255 heads, 63 sectors/track, 821310538 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xedaaedaa

Disk /dev/sdb doesn't contain a valid partition table

```

Thanks for all of your help, but I'm still confused!

---

### Post by alphaniner on 2009-10-29
```
Disk /dev/sdb: -1834425450 MB, 6755509142683648 bytes
```

All I can say is LOL.

There's definitely something wrong with that drive.  Switch back to the other one.

If you are having trouble with **cfdisk**, try another tool, **parted**.

First, do **sudo fdisk -l** again and make sure see

```
Disk /dev/sdb doesn't contain a valid partition table
```

This way we make absolutely sure we are not messing up your system drive.  If you see that line, you can then use these commands exactly as I type them:

```
sudo parted /dev/sdb mklabel msdos
sudo parted /dev/sdb mkpart primary 0 100%
```

Then post the output of **sudo fdisk -l** again so we can make sure things have gone ok so far.

---

### Post by Joseph Schwenker on 2009-10-29
> **alphaniner said:**
> ```
Disk /dev/sdb: -1834425450 MB, 6755509142683648 bytes
```

All I can say is LOL.

There's definitely something wrong with that drive.  Switch back to the other one.

If you are having trouble with **cfdisk**, try another tool, **parted**.

First, do **sudo fdisk -l** again and make sure see

```
Disk /dev/sdb doesn't contain a valid partition table
```

This way we make absolutely sure we are not messing up your system drive.  If you see that line, you can then use these commands exactly as I type them:

```
sudo parted /dev/sdb mklabel msdos
sudo parted /dev/sdb mkpart primary 0 100%
```

Then post the output of **sudo fdisk -l** again so we can make sure things have gone ok so far.

The other drive said that it was bigger than it really was, too.  Plus, there is NO WAY I am going back to that drive.  It was LOUDER THAN MY ENTIRE COMPUTER!  Besides, I have already backed up all of my data onto disks.  I guess I'll be using disks forever.  :'(
Thanks for everyone's help!

---

### Post by alphaniner on 2009-10-29
Ok.  Good luck.

---

### Post by ezsit on 2009-10-29
> AAAAAAAAAAAAHHHHHHHHH!!! This is too confusing! You are talking about commands like there are as common as air! Could you please explain to me how to do what ezsit told me to do? It didn't make much sense. I can't figure out how to use the cfdisk.

Sorry for the lack of explanation. Its been a long time since my first encounter with cfdisk and partitioning that I forget some people are just learning the stuff.

To start cfdisk from the terminal windows, use **sudo cfdisk /dev/sdb**. I am assuming your drive shows up as sdb1 from previous fdisk -l output. cfdisk works on the entire drive so you do not specify partitions, just the entire device when calling cfdisk.

The terminal will fill up with the cfdisk program running and present the list of partitions and free space in the center of the display. Along the bottom of the screen will be choices for actions to take.

Since I am not at my Linux box, I cannot take screen shots for cfdisk. However, cfdisk is not difficult if you pay attention to what you are doing. 

Use the UP/DOWN arrow keys to select partitions or free space regions to work on by moving the highlight up and down. Use the LEFT/RIGHT arrow keys to select from along the bottom of the screen choices to select an action to take.

When the screen changes to filesystem type for the partition, use the SPACE BAR to continue to the next screen and use TYPE 83 for Linux partitions and TYPE 82 for SWAP (default is 82, so beware!!!). I believe TYPE 0B is for FAT32 and TYPE 07 is for NTFS (but I'm not too positive for those since I no longer have Windows sharing the same box as Linux).

When finished with cfdisk, make sure to select WRITE CHANGES TO DISK before quitting.

cfdisk does not actually format the partitions, it merely writes the filesystem type into the partition. You will need to use another command to format the partitions, mkfs. To format a partition for ext3, type:

**sudo mkfs.ext3 /dev/sdb1**  -- assuming the first primary partition on sdb is the target of your desires.

**sudo mkfs.vfat /dev/sdb1** -- this will format the partition for use with the FAT32 filesystem, only do this if you correctly set the partition type to FAT32 when in cfdisk.

Hope this helps.

---

### Post by louieb on 2009-10-29
Did you check the jumper settings. (Master/Slave) You will need to check both drives.

---

