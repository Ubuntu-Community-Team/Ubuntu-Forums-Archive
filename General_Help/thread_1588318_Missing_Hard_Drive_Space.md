---
title: "Missing Hard Drive Space"
date: 2010-10-04
forum: General Help
---

### Post by Erebus1 on 2010-10-04
I have an internal 1 TB Western Digital Caviar Green Hard drive in my computer.  On it, I partitioned off 150 GB to allow for dual booting Windows, and the other 850 GB for running Ubuntu 10.04.  
I noticed that the amount of free space (591.9 GB) seemed a bit small, since my home folder only takes up 130.6 GB.  I checked how much space to OS took up, 6.3 GB, and I realized that I have about 111.3 GB not accounted for. 

If anyone would be able to explain how I could access this information, with instructions for someone relatively noobish, I would be very appreciative.

---

### Post by nevius on 2010-10-04
> **Erebus1 said:**
> I have an internal 1 TB Western Digital Caviar Green Hard drive in my computer.  On it, I partitioned off 150 GB to allow for dual booting Windows, and the other 850 GB for running Ubuntu 10.04.  
I noticed that the amount of free space (591.9 GB) seemed a bit small, since my home folder only takes up 130.6 GB.  I checked how much space to OS took up, 6.3 GB, and I realized that I have about 111.3 GB not accounted for. 

If anyone would be able to explain how I could access this information, with instructions for someone relatively noobish, I would be very appreciative.

There are 1024 megabytes in a gigabyte. One terabyte is 1024 gigabytes. Marketing types treat these values as 1000. This accounts for some of the missing space. I'm too lazy to do the math to figure out how much it accounts for.

---

### Post by Erebus1 on 2010-10-04
> There are 1024 megabytes in a gigabyte. One terabyte is 1024 gigabytes. Marketing types treat these values as 1000. This accounts for some of the missing space. I'm too lazy to do the math to figure out how much it accounts for.
Well, if I'm not rounding the total capacity of the Linux partition, then it's full capacity is ~839.9 GB, the full capacity for the Windows partition is ~150.2 GB.  The Linux OS and my home folder add up to a total of ~136.8 GB, and it says that there are 591.9 GB available.  That means that there are ~111.2 GB still unaccounted for.

---

### Post by nevius on 2010-10-04
Post the output of ```
sudo fdisk -l
```

---

### Post by Erebus1 on 2010-10-04
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x69205244

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18261   146681066    7  HPFS/NTFS
/dev/sda2           18262      121602   830080001    5  Extended
/dev/sda5           18262      120378   820253696   83  Linux
/dev/sda6          120379      121602     9825280   82  Linux swap / Solaris

---

### Post by warfacegod on 2010-10-04
Ubuntu by default sets a system reserve of 5% on all partitions (I don't know if it does this to NTFS/Windows installed partitions or not.) 5% of 1 TB is about 50 GB. You also have a swap partition so there is another fairly sizable chunk. You now know where at least some of that space went.

---

### Post by jfed on 2010-10-04
I think the reason for this is the same as the first poster said. If you notice when you buy a 4gig flash drive, it has 3.9megs of space. This is because companies market their drives with their own stupid little spacing. 1,000kb = 1mb. 1,000mb = 1gb. I don't know who came up with this, because their 24units off, which can make a big difference when you're dealing with huge hard drives.

---

### Post by Erebus1 on 2010-10-04
> **warfacegod said:**
> Ubuntu by default sets a system reserve of 5% on all partitions (I don't know if it does this to NTFS/Windows installed partitions or not.) 5% of 1 TB is about 50 GB. You also have a swap partition so there is another fairly sizable chunk. You now know where at least some of that space went.



Right; When I open up the disk utility, it shows the way the disk is divvied up: 150 GB for Windows, 840 GB for Linux, and 10 GB for a "swap space."  Then, looking in the filesystem, the OS is ~6.2 GB, and the home folder is ~130.6 GB, and there is 591.9 GB available.  That adds up to ~111.2 GB still missing.

---

### Post by nevius on 2010-10-04
```

1953520065 SECTORS or 1000202273280 bytes or 931.51 gigabytes
NTFS = 150201838080 bytes or 139.89 gigabytes
SDA2 EXTENDED = 850000435200 bytes or 791.62 gigabytes
LINUX = 839940917760 or 782.25 gigabytes
SWAP = 10059517440 or 9.37 gigabytes

NTFS + SDA2 = 1000202273280 bytes or 931.51 gigabytes
NTFS + LINUX + SWAP = 1000202273280 bytes or 931.51 gigabytes
```
TRANSLATION:

FDISK is showing all of your hard drive space is accounted for. Your hard drive is either 931.51 gigs or 1 terabyte based on how you calculate it. If we take it optimistically (the marketing way), you have 150GB for your windows partition, 840GB for your Linux partition, and 10GB for your swap. Nothing is missing. You do have a little more space allocated to swap than I would use.

CAVEAT:

I am tired and I am not a mathematician. Feel free to correct my calculations.

UPDATE:

~70GB of the missing hard drive space is probably due to the different ways of counting GB. ~40 gb can be accounted for by a 5% system reserve the partitions.

---

### Post by psusi on 2010-10-04
> **warfacegod said:**
> Ubuntu by default sets a system reserve of 5% on all partitions (I don't know if it does this to NTFS/Windows installed partitions or not.) 5% of 1 TB is about 50 GB. You also have a swap partition so there is another fairly sizable chunk. You now know where at least some of that space went.

Bingo.

The kernel won't allow non root users to invade the last 5% of the disk, so it reports 5% less available space to them.

---

### Post by warfacegod on 2010-10-05
Disk Utility is showing you space in fake GB as 1,000 bits per. Just like HDD companies do. This is one of several serious flaws with Disk Utility.

The problem is that the file browser and pretty much the rest of the OS don't do this. They use real GB. Just like every other computer hardware company does.

You are comparing two completely different and incompatible sets of numbers.

The reality is that you have a 931 GB HDD.

> 1953520065 SECTORS or 1000202273280 bytes or **931.51 gigabytes**

This is consistent with all other 1 TB HDD's. For example, my 1 TB External is really 934 GB.

Now that we have established that Disk Utility and the HDD companies are full of crap and that you actually have 931 GB you may notice that you are still "missing" some space.

Some of this is the swap partition. (This basically acts as RAM on your HDD.) Most of it is due to the system reserve. And any left over will be due to the HDD's format. Different formats (filesystems) such as ext4, NTFS, and FAT32 all use up space and they all use different amounts of space.

---

### Post by TNT1 on 2010-10-05
> **psusi said:**
> Bingo.

The kernel won't allow non root users to invade the last 5% of the disk, so it reports 5% less available space to them.

Why exactly?

---

### Post by warfacegod on 2010-10-05
It's a safety thing. It is absolutely never a good idea to completely fill an HDD. It causes all sorts of bad things to happen. Heavy file fragmentation, data loss, etc. The 5% system reserve acts as a buffer and stops this from happening.

---

### Post by Erebus1 on 2010-10-05
Oh.  OK, thanks for the information.  

<being_ridiculous_for_the_hell_of_it>
Does this mean that I can sue Western Digital for $6.32, since they said I was getting more than I actually did?  
</being_ridiculous_for_the_hell_of_it>

---

### Post by psusi on 2010-10-05
> **Erebus1 said:**
> Oh.  OK, thanks for the information.  

<being_ridiculous_for_the_hell_of_it>
Does this mean that I can sue Western Digital for $6.32, since they said I was getting more than I actually did?  
</being_ridiculous_for_the_hell_of_it>

Unfortunately no, hd manufacturers have always labled disks this way and argue that it is everyone ELSE who is using the wrong definition of a kilo/mega/giga/terra byte.

---

### Post by Erebus1 on 2010-10-05
> Unfortunately no, hd manufacturers have always labled disks this way and argue that it is everyone ELSE who is using the wrong definition of a kilo/mega/giga/terra byte.

<still_being_ridiculous>
KAHN!!
</still_being_ridiculous>

---

### Post by psusi on 2010-10-05
lulz.

---

### Post by 55tptag on 2010-10-05
What filesystem are you using? I couldn't figure it out when you ran
```
sudo fdisk -l
```

If you don't know please run ```
sudo parted -l
```

If you have ext2/ext3 filesystems you can modify the amount of space Linux reserves for its own use.  (note:The man page for tune2fs says it can modify the tunable filesystem parameters on ext2/ext3/ext4 filesystems.  I just have never done it on ext4 before)

The command to run so that you can reclaim some disk space is tune2fs.

Before I ran the command on my 500GB drive it showed as the following.  Note "Used" and "Avail". My home partition is on sdb1:
```
# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             459G  409G   27G  94% /home

```

But, I wanted to use all of the space.  So, I reduced the size that root reserves from 5% to 0% with the following command:
```
# tune2fs -m 0 /dev/sdb1
tune2fs 1.41.11 (14-Mar-2010)
Setting reserved blocks percentage to 0% (0 blocks)
```

After,```
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             459G  409G   50G  90% /home
```

So, I now have "Used 409G" + "Avail 50G" =  "Size 459G". 

If you're wondering why it shows up at a size of 459G and not 500GB see, [http://en.wikipedia.org/wiki/Gigabyte]("http://en.wikipedia.org/wiki/Gigabyte"), especially the part on Consumer confusion.

Also, read about Gibibyte at [http://en.wikipedia.org/wiki/Gibibyte]("http://en.wikipedia.org/wiki/Gibibyte").

---

### Post by warfacegod on 2010-10-05
tune2fs works just fine on ext4. I've used it many times.

**Fair Warning:** It is extremely unwise to change the system reserve to 0% on the partition that the OS resides on. Doing it on a separate partition for /home is fine as long as you remember that there is no reserve once you start getting to the end of your drive space.

---

