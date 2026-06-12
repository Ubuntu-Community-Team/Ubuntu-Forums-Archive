---
title: "More than four primary partitions"
date: 2011-07-25
forum: General Help
---

### Post by dwally89 on 2011-07-25
Hi,

I just bought a new laptop and it comes with four primary partitions already (Main partition, HP Tools, Recovery and System).
I want to create another partition to store my data on, as I like to have my OS and programs on one partition, and my data on another, but I can't create another partition as I already have 4 primary partitions.
Is there a way that I can change one of these partitions into an extended partition without losing any of the data on them?

Thanks

---

### Post by coffeecat on 2011-07-25
> **dwally89 said:**
> 
Is there a way that I can change one of these partitions into an extended partition without losing any of the data on them?


No. You have to delete a primary before you can create an extended. If your HP is anything like my HP, then your partition layout is:

sda1 - Windows 7 boot partition. (labelled "System")
sda2 - Windows C: partition.
sda3 - Recovery partition.
sda4 - HP_TOOLS partition.

You need the Recovery partition to do a restore to factory default. And you need the hp_tools partition to create a set of recovery DVDs. So as not to type this all out again, this is what I did (posted in another thread):

[http://ubuntuforums.org/showpost.php?p=11025958&postcount=11](http://ubuntuforums.org/showpost.php?p=11025958&postcount=11)

You lose a little space at the end of the drive by doing this, but the HP_TOOLS partition is very small, so you don't lose much. But before you do anything boot up with an Ubuntu live CD or USB and post the terminal output of:

```
sudo fdisk -lu
```

And/or post a screeshot of a Gparted window. Then we can see exactly what your partition layout is like and whether it is the same/similar to my original HP one.

---

### Post by dwally89 on 2011-07-25
```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18f50e1a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      409599      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          409600   936472575   468031488    7  HPFS/NTFS
/dev/sda3       936472576   976560127    20043776    7  HPFS/NTFS
/dev/sda4       976560128   976771119      105496    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ 

```

According to gparted,
sda1 is SYSTEM
sda2 is unlabeled
sda3 is RECOVERY
sda4 is HP_TOOLS

---

### Post by coffeecat on 2011-07-25
Yes, your partition layout seems to be the same as originally on my HP mini with the exception of the sizes of the partitions. Your sizes are:

sda1 - 209MB
sda2 - 479GB
sda3 - 20.5GB
sda4 - 108MB

Those are MB/GB (base 10), not MiB/GiB (base 2).

If you follow my suggestion and remove sda4, you should then shrink sda2, the Windows C: partition, from within Windows with its Disk Management tool. This is safer than using Gparted. There's nothing particularly wrong with Gparted but Windows can react badly to its own partition being resized with anything but its own utility. You can then create an extended partition in the space freed up by using Gparted - don't use the Windows Disk Management for this bit! You will lose the 108MB at the end of the disk, but that is only a small amount in comparison with the 500GB size of your hard drive. In theory you could move sda3 to the right by 108MB to reclaim the 108MB but I wouldn't recommend it. 

The alternative is to do what some HP owners do and that is to delete your recovery partition. If you make sure you create a set of recovery discs first you should still have the same functionality - it's your choice - but you will lose your recovery partition, obviously.

---

### Post by dwally89 on 2011-07-25
> **coffeecat said:**
> Yes, your partition layout seems to be the same as originally on my HP mini with the exception of the sizes of the partitions. Your sizes are:

sda1 - 209MB
sda2 - 479GB
sda3 - 20.5GB
sda4 - 108MB

Those are MB/GB (base 10), not MiB/GiB (base 2).

If you follow my suggestion and remove sda4, you should then shrink sda2, the Windows C: partition, from within Windows with its Disk Management tool. This is safer than using Gparted. There's nothing particularly wrong with Gparted but Windows can react badly to its own partition being resized with anything but its own utility. You can then create an extended partition in the space freed up by using Gparted - don't use the Windows Disk Management for this bit! You will lose the 108MB at the end of the disk, but that is only a small amount in comparison with the 500GB size of your hard drive. In theory you could move sda3 to the right by 108MB to reclaim the 108MB but I wouldn't recommend it. 

The alternative is to do what some HP owners do and that is to delete your recovery partition. If you make sure you create a set of recovery discs first you should still have the same functionality - it's your choice - but you will lose your recovery partition, obviously.

I used GParted to shrink my Windows partition, and deleted the HP tools one, and create a new data partition (leaving the 108MB at the end free), and all seems to be ok so far

Thanks

---

### Post by coffeecat on 2011-07-25
> **coffeecat said:**
> you should then shrink sda2, the Windows C: partition, from within Windows with its Disk Management tool. This is safer than using Gparted. There's nothing particularly wrong with Gparted but Windows can react badly to its own partition being resized with anything but its own utility.

> **dwally89 said:**
> I used GParted to shrink my Windows partition, and deleted the HP tools one, and create a new data partition (leaving the 108MB at the end free), and all seems to be ok so far

You were lucky not to make Windows unbootable - seriously!

Anyway, you've created a data partition? If that's a primary partition, you're back at square one. I was assuming you would use the space freed by shrinking the Windows partition to make an extended partition in which you could make a number of logical partitions for Linux and for data. Post back if you need any help with that.

---

### Post by dwally89 on 2011-07-25
> **coffeecat said:**
> You were lucky not to make Windows unbootable - seriously!
GParted has been good to me in the past.
I didn't move the Windows partition, just shrank it. When I then booted up into Windows, it did a quick scan for errors, and then everything was fine.

> **coffeecat said:**
> Anyway, you've created a data partition? If that's a primary partition, you're back at square one. I was assuming you would use the space freed by shrinking the Windows partition to make an extended partition in which you could make a number of logical partitions for Linux and for data. Post back if you need any help with that.

Yeah, I intended to create a data partition. Am not going to be installing Linux at the moment, and if I do it at a later date, it'll be through Wubi.

Thanks for the help again

---

### Post by Quackers on 2011-07-25
> **dwally89 said:**
> GParted has been good to me in the past.
I didn't move the Windows partition, just shrank it. When I then booted up into Windows, it did a quick scan for errors, and then everything was fine.

Lol, I'll bet it did :-)

Maybe we should have a Windows only section of the forum :-)

---

### Post by dwally89 on 2011-07-25
> **Quackers said:**
> Maybe we should have a Windows only section of the forum :-)

To be honest, this question was just as relevant to any operating system, it wasn't specifically a Windows question.
My question was simply:
If you already have four primary partitions on a hard drive, is it possible to turn one of them into an extended partition without losing data?

No mention of Windows (or any other operating system) there.

---

### Post by CatKiller on 2011-07-25
> **dwally89 said:**
> Yeah, I intended to create a data partition. 

It's probably worth creating an extended partition with that partition inside it before you put anything on it. That way you can add more partitions later without having to delete any.

---

