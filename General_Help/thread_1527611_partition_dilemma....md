---
title: "partition dilemma..."
date: 2010-07-09
forum: General Help
---

### Post by x-shaney-x on 2010-07-09
After taking delivery of a new laptop, I immediately ran ubuntu from a live cd, eager to shrink down the windows partition to make room for my linux.
Unfortunately, I have run into a MAJOR problem:

The disk is partitioned like so:
```

/dev/sda1  -  ntfs  -  system  -  199mb
/dev/sda2  -  ntfs  -  windows 7  -  285gb
/dev/sda3  -  ntfs  -  recovery  -  12.5gb
/dev/sda4  -  fat32  -  hp tools  -  102mb
```

This leaves me with several problems:
The only thing I can really do is delete the recovery and tools partitions, then shrink down the windows partition to give me room to create a new extended partition.

Trouble is I really didn't want to interfere with the system partitions.
Not only that, the comp didn't come with a Windows installation disk, which means if I mess up I no longer have a recovery partition to sort it out.

My previous comp used half the disk for windows with a recovery partition and the rest of the disk was left unallocated which made things much easier because I could leave those partitions untouched.

What to do?

---

### Post by Vincentlaborant on 2010-07-09
First you should enter Windows to make a complete back up of your windows. This will require several dvd's. Or u clone the disk with Clonezilla, which you can use from ubuntu and windows.

The normal route is to create the recovery dvd's with Windows 7 back up center. Normally a pop up should appear after the first time loading of Windows that you have to make a back up.

After creating the back up, you run the live-cd of Ubuntu and format the entire hard drive and be sure to create 2 partitions. Now do a custom install of Windows, since the Windows MBR ****s up the Grub bootloader. Be sure to select only 1 partition you created to be used during the Windows installation.

After the Windows installation, you get the Ubuntu live-cd back in the dvd player and do a custom install of Ubuntu, on the second partition. After that, you can do what you like.

---

### Post by x-shaney-x on 2010-07-09
When you say do a custom installation of windows...
Does this mean if I create the recovery backup within windows, I can then use those disc to re-install windows?
Otherwise I have no way to re-install it since it didn't come with a disc.

---

### Post by mike555 on 2010-07-09
probably be safer to back up the "tools" partition onto a thumbdrive ,then delete the partition then in 7 shrink your big partition and create a partition for Ubuntu (maybe half) and install Ubuntu there ..


 I would still backup totally first -just in case.

---

### Post by x-shaney-x on 2010-07-09
Thanks for the suggestions.

I backup up every partition to be on the safe then deleted the two partitions I mentioned, shrank the windows one and am now typing this from a fresh ubuntu install.
Everything is working fine ubuntu and windows-wise (well as far as I can tell, so long since I've used windows I don't know what it's meant to do anymore).

---

### Post by Vincentlaborant on 2010-07-09
> **x-shaney-x said:**
> When you say do a custom installation of windows...
Does this mean if I create the recovery backup within windows, I can then use those disc to re-install windows?
Otherwise I have no way to re-install it since it didn't come with a disc.

When you make the backup of windows (step 1) you have your recovery settings on dvd's or an external hard drive. As long as the media is intact and not changed, you will have a recovery option ready to use.

Then, whenever it is necessary, you can re-install windows using that media, or restore windows to the original settings with it. Off course, you will have to make back ups of your files regularly, so you never lose data. I also recommend making a extra new system recovery back up of windows after installing a service pack for your operating system. Then you can bring windows back to life without the frustration of updating the computer for almost a day.

A custom installation mean you select the drive/ partition where windows is installed. So you select everything, because Windows uses a hole hard drive by default. So, in order to be able to set up a dual-boot system, you will have to do a custom install, unless you want to do a resizing of your windows install (which is also easy, but a little bit more trickier than my option).

---

