---
title: "Repartitioning Hard Drive"
date: 2010-09-21
forum: General Help
---

### Post by Turwaithien on 2010-09-21
Hi. I'm trying to repartition the hard drive so I can dual-boot windows. I'm using a live-cd-usb so the hard drive is not mounted. I run gparted and it does the filesystem check which is fine (or at least seems fine), but it fails at actually resizing the drive.

Here's the log file:
[GParted Details]("http://ubuntuone.com/p/H2H/")

I don't know what other information I should provide.

---

### Post by Dustin2128 on 2010-09-21
what are you using a livecd of, ubuntu or gparted?

---

### Post by Jesus_Valdez on 2010-09-21
I think that the easier way of doing this is installing Windows first (take over the entire HD) and then re-install ubuntu.

---

### Post by Turwaithien on 2010-09-21
I'm using a Ubuntu live-cd.

I would much rather not install windows over the whole thing. Even with all the files backed up, I'd still lose all the settings and programs and personality. I only really want about 20 GB for windows, specifically just so I can play a game.

If there isn't a way to do this without losing Ubuntu, I don't think I will.

---

### Post by spiky001 on 2010-09-21
you should be able to right click on the partition you want shrink then there is an option to resize it some1 correct me if i,m wrong

---

### Post by Dustin2128 on 2010-09-21
If you don't already have one, you should burn a knoppix disc. It usually works great with disc partitioning and other operations that must be carried out in live mode. For some reason, it often works where gparted live fails :?

---

### Post by Turwaithien on 2010-09-21
I shall try the knoppix!

---

### Post by Dustin2128 on 2010-09-21
> **Turwaithien said:**
> I shall try the knoppix!
you could also always try the cfdisk terminal partitioning tool, once you're on knoppix. Its what I always use with command line installs like gentoo and slackware.

---

### Post by srs5694 on 2010-09-21
AFAIK, cfdisk doesn't have any filesystem management tools. Thus, even though you can resize the a *partition* in cfdisk, the *filesystem* it contains won't be resized. This results in a pointless change if you increase the size of a partition and a very dangerous misconfiguration if you decrease it.

You can use resize2fs to resize a filesystem along with cfdisk (or fdisk or various other tools) to resize the containing partition, but that's much more work than using GParted or parted, which perform both operations at once.

---

### Post by Turwaithien on 2010-09-21
> **srs5694 said:**
> AFAIK, cfdisk doesn't have any filesystem management tools. Thus, even though you can resize the a *partition* in cfdisk, the *filesystem* it contains won't be resized. This results in a pointless change if you increase the size of a partition and a very dangerous misconfiguration if you decrease it.

You can use resize2fs to resize a filesystem along with cfdisk (or fdisk or various other tools) to resize the containing partition, but that's much more work than using GParted or parted, which perform both operations at once.

It looks like Gparted runs resize2fs and fails at the resizing. How do I fix that?

---

### Post by perspectoff on 2010-09-21
> **Jesus_Valdez said:**
> I think that the easier way of doing this is installing Windows first (take over the entire HD) and then re-install ubuntu.

I strongly, strongly disagree. Never let Windows take over the whole drive (if you can help it), especially with Windows Vista or Windows 7.

If you do that it becomes difficult to shrink the Windows (Vista or 7) partition later.

It is much better to partition the drive first (properly). Install Windows into the first partition second. Install (K)Ubuntu third.

GParted runs the same no matter whether it runs from the (K)Ubuntu Desktop LiveCD or from the GParted LiveCD (which uses Knoppix as the base OS, not Ubuntu).

---

### Post by perspectoff on 2010-09-21
> **Dustin2128 said:**
> If you don't already have one, you should burn a knoppix disc. It usually works great with disc partitioning and other operations that must be carried out in live mode. For some reason, it often works where gparted live fails :?

Nah, that's nonsense. Knoppix is a fast OS, but GParted works the same from the Knoppix LiveCD as from the Ubuntu LiveCD, at least the Ubuntu Desktop LiveCD.

Using the command-line only version of GParted is a bit painful. Is there a reason you need to do that?

I highly recommend using the graphical version of GParted, which on the Ubuntu Desktop LiveCD is started:

Menu -> System -> Administration -> GParted

You then get to see all your partitions in a nice GUI (just like on the Knoppix-based GParted LiveCD).

I guarantee that usage is much more intuitive that way.

---

### Post by Dustin2128 on 2010-09-21
> **perspectoff said:**
> Nah, that's nonsense. Knoppix is a fast OS, but GParted works the same from the Knoppix LiveCD as from the Ubuntu LiveCD.
hum, maybe I just had a corrupted disk. It's still a good idea to keep a knoppix disc around anyway.

---

### Post by perspectoff on 2010-09-21
> **Dustin2128 said:**
> hum, maybe I just had a corrupted disk. It's still a good idea to keep a knoppix disc around anyway.

I'm not necessarily disagreeing with you. I have loved the Knoppix-based GParted LiveCD for many, many years, and Knoppix is a lickety-split version of Linux.

But this is Ubuntu forums and trying to get newbies to download and burn a Knoppix-based LiveCD disk in addition to their Ubuntu LiveCD is just a bit much to ask, IMO.

---

### Post by Turwaithien on 2010-09-21
> **perspectoff said:**
> Nah, that's nonsense. Knoppix is a fast OS, but GParted works the same from the Knoppix LiveCD as from the Ubuntu LiveCD, at least the Ubuntu Desktop LiveCD.

Using the command-line only version of GParted is a bit painful. Is there a reason you need to do that?

I highly recommend using the graphical version of GParted, which on the Ubuntu Desktop LiveCD is started:

Menu -> System -> Administration -> GParted

You then get to see all your partitions in a nice GUI (just like on the Knoppix-based GParted LiveCD).

I guarantee that usage is much more intuitive that way.

That's what I did. I didn't really know how to go about doing it via command line.

---

### Post by Turwaithien on 2010-09-21
If I do have to format the whole drive, is there any way I can back up Ubuntu in a way that I would not have to start completely over?

---

### Post by perspectoff on 2010-09-21
So here's what I do with a new computer (with a boxed retail version of Windows and a virgin hard drive).

Using the GUI version of Gparted from the Ubuntu LiveCD (or the Knoppix GParted LiveCD), I create an NTFS primary partition for Windows (no reason to use FAT32 anymore). I tend to make this a bare minimum of 30 Gb, since Windows Vista installs for me as 22 Gb, and Windows 7 just a bit more. This is always the first partition (a habit from the days when Windows insisted on being the first partition) and I make sure the "boot" flag is set for this partition. (These options are all obvious in the GUI version of GParted).

I then make a second small primary partition, of any size (perhaps 200 Mb), just as a place holder. I tend to leave this as FAT32, only because most consumer retail computers have a second partition for their diagnostic tools in a FAT32 partition here. Some users may want to re-create whatever they got from their retailer later, so I leave this in place. The "boot" flag does not need to be set for this partition (only the main Windows partition needs the "boot" flag to be set.)

Because many retail computers come with the first two primary partitions already installed, as long as there is enough additional space on the  hard drive, I tend to leave these first two partitions alone (i.e. without shrinking them) if they are already set up. 

I then create a 100 Mb primary partition as my third partition. On all my computers, I use this small partition ( the "boot" partition) in which to store a master bootloader. (Setting up a master bootloader is somewhat of a complex process the first time, but it saves lots and lots of problems in the long run.) The "boot" flag does not need to be set for this partition.

It is not really necessary to use a boot partition at all, but it is nice to create it at the outset (so if one chooses to use it later, it will be already in place).

The fourth partition will be an extended partition. An extended partition can then be subdivided into many logical partitions. Within the extended partition I then create a single 2 Gb linux-swap partition (always) and then the remainder of the extended partition is used to create an ext4 or ext3 partition which then will be used for the (K)Ubuntu OS. 

Additional logical partitions can optionally be created (at this point or even at any later time) as long as there is space left within the extended partition. Logical partitions can be moved, re-arranged, shrunk, grown, (or whatever), with maximum flexibility, depending on one's tastes.

(K)Ubuntu and other Linux OSs (but not Windows) can be installed in logical partitions, so I highly recommend this scheme.

Once the partitions are all set up, then I install Windows to the first partition.

This works fine with a boxed retail version of Windows.

But here is the sticky wicket: some recovery disks supplied with some computers use an OEM version of Windows that insists on reformatting the entire disk all over again (destroying all the carefully created partitions) and then, indeed, installs Windows to the entire hard drive. (That sucks, and seems to be part of the Microsoft imperialist master plan.) In this case, the single Windows partition indeed has to be once again shrunk (I use Perfect Disk for this, since it can move the Vista/7 MFT successfully and can therefore gain a significant amount of hard drive back, which can't be done using the Windows Disk Management utility).

Windows XP (or older) can use GParted (as above) to shrink its partition. 

If I have needed to shrink a Windows partition, I then always reboot once (or twice, to be safe) so that Windows can store the changed partition size information, prior to doing anything else.

Then I create the additional partitions (as outlined above) by restarting GParted from a LiveCD.

Finally I re-start the (K)Ubuntu LiveCD, this time in installation mode (instead of demo mode) and proceed with installing Ubuntu into the logical drive I have created for it.

After nearly 300 installations of Ubuntu, with some computers containing up to 7 operating systems on them simultaneously, this method is the most flexible, robust, and failsafe for me.

Of course, I use a master bootloader in the boot partition, to which the Master Boot Record always refers, as mentioned before, so that I can easily load any OS and not worry about all the secondary bootloaders competing with each other. But that is a special technique that takes some attention and is outlined at

[http://ubuntuguide.org/wiki/Ubuntu:All#Installing_multiple_OS_on_a_single_computer](http://ubuntuguide.org/wiki/Ubuntu:All#Installing_multiple_OS_on_a_single_computer)

or

[http://kubuntuguide.org/All#Installing_multiple_OS_on_a_single_computer](http://kubuntuguide.org/All#Installing_multiple_OS_on_a_single_computer)

---

### Post by perspectoff on 2010-09-21
> **Turwaithien said:**
> If I do have to format the whole drive, is there any way I can back up Ubuntu in a way that I would not have to start completely over?

Yes, you can copy the entire partition with Ubuntu in it using partimage. See

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#System_Backup_and_Recovery](http://ubuntuguide.org/wiki/Ubuntu:Lucid#System_Backup_and_Recovery)

Unfortunately, I don't think partimage is available on the LiveCD, and I have never had to do that so am not exactly sure which LiveCD would have it available. I doubt you can copy any partition using the OS that is running from within it. 

All my computers have at least two copies of (K)Ubuntu on them, so I can copy the partition with one version of Ubuntu from the other partition (using partimage).

SystemRescueCD may have partimage on it; I'm not sure. You'll have to do that bit of research yourself, I'm afraid.

To be honest, installing Ubuntu has never taken me more than about an hour, except on production systems that I have been using for a while. (On those systems it takes me about 3 weeks to successfully reinstall or upgrade successfully).

It will probably take you less time (if you are a relatively new user) to re-install and re-customise Ubuntu than to copy the partition somewhere and then copy it back. But YMMV.

---

### Post by srs5694 on 2010-09-21
> **Turwaithien said:**
> It looks like Gparted runs resize2fs and fails at the resizing. How do I fix that?

I took another look at the log file you posted, and I noticed this:

```

resize2fs: Attempt to read block from filesystem resulted in short read while trying to resize /dev/sda1
Please run 'e2fsck -fy /dev/sda1' to fix the filesystem
after the aborted resize operation.

```

First, I suggest you run the e2fsck command specified in the message. There's a chance that this will solve the problem and allow a subsequent run to succeed.

Unfortunately, Googling on that error message suggests what I feared from reading it: It's most likely a hardware fault. I recommend using a utility that can read the SMART status of the drive, such as gsmartcontrol or smartctl. Check the error log and look for other signs of failure, such as more than a tiny number of reallocated sectors. If I'm right and this is a hardware failure, you should buy a new disk *immediately* and use a disk-cloning utility to copy Ubuntu onto the new disk. You should be able to size Ubuntu appropriately on the new disk as you do the copy, leaving room for Windows; or you could partition the new disk, install Windows on it, and then copy Ubunto.

---

### Post by Turwaithien on 2010-09-22
```
ubuntu@ubuntu:~$ sudo e2fsck -fy /dev/sda1
e2fsck 1.41.11 (14-Mar-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
/dev/sda1: 264766/7143424 files (3.9% non-contiguous), 15960635/28559545 blocks

```

This is what shows up for e2fsck. Running GParted still does the same thing.

I am somewhat unsure as to how to work the smart data thing. It's kind of late though, so my brain is becoming squishy. I'll try to work it out later.

---

