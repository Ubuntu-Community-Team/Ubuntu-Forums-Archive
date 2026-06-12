---
title: "Ubuntu and WinXP - Dual boot"
date: 2006-01-22
forum: General Help
---

### Post by tico on 2006-01-22
I've already read some threads about this, but I think my case is a bit more concrete. I already have WinXP installed and configured and some data in my box. I'd like to install Ubuntu and mantain my WinXP install. I'm afraid of installing Ubuntu and of losing all my stuff (too hard to configure...). Is it possible to install Ubuntu in this case and mantain my WinXP installation? Will I be able to boot using Windows dual boot or I'll need to use Ubuntu's own boot manager?:confused: 
TIA for helping me.

---

### Post by aysiu on 2006-01-22
Yes, yes, yes, and yes, if you follow the instructions in the fifth link of my signature.

However, I would still advise you to back up all your important data. Even when you're just doing everyday stuff, it's a good idea, but especially if you're messing about with partitions and dual booting and you've never done it before.

Burn discs, buy 100 floppies, upload to the internet, use zip drives, iPods, whatever, but **please** back up your stuff.

---

### Post by dcast on 2006-01-22
this perfectly possible. You just need a partition and during the install you can choose to install to that partition. with grub (the bootloader) install you should automatically be given the choice between windows and ubuntu at startup.

---

### Post by christooss on 2006-01-22
Ofcourse you can install Ubuntu and keep Windows on its place.

First you have to repartition your disk. On one partition you still have Windows and other partition will have Ubuntu. Make shure you format this other partition in Fat32 so Install CD will see it.

Than when installation promts you about partitioning make shure that you choose manual parititioning. Than it asks you on which partition you want to install Ubuntu make shure you choose Fat32 partition.

Than Grub wiil be installed as a Boot manager. And when booting system will automaticly get in Ubuntu. There you will simply edit Grub to boot in Windows

---

### Post by christooss on 2006-01-22
Like aysiu sad please DO BACKUP but I don't think it will be nessesary

---

### Post by tico on 2006-01-23
Thanks to everybody!! :) 

I'll try to install Ubuntu in some days (I need to back up everything and find some space for Ubuntu - my box is completely full).
Another question: are you using only Ubuntu or do you still use Windows? I probably will not be able to abandon Windows because some of my most important software work only on Windows (maybe it will be possible to run them using Wine or an emulator - do you have any experience on that?). I'm glad that Ubunt recognizes my hardware. I'm trying to use Linux since 98, but I've always had hardware (and software, as I described) problems. At least now my hardware seems to work fine (I tested it with the LiveCD - I should also check my digital cam).

So, are you still using Windows?

Many thanks for your help.

---

### Post by christooss on 2006-01-23
I am on [the NO windows list :)](http://ubuntuforums.org/showthread.php?t=6894)

---

### Post by Luke771 on 2006-01-23
if your hd is full, maybe the right thing could be add another hard drive and install Ubuntu on that one. doing so you don't need to do anything on your old drive, just add another one and configure them as master (the old one) and slave (the new one) without partitioning anything (i.e. no partitions and 100% free space on the new drive) then install Ubuntu, when you get to the partitioning part, manually edit the partition table, leave alone all the entries marked as hda-something (that's the old drive), install the OS on the free space on hdb an the installer will do the rest. easy.
If you want to have a FAT32 partition on the new drive, for data accsess with both OSes, then you 'll have to make it manually during the install (fairly easy) or use some Partition Magic kind of thing (sueper-easy) and make the FAT32 partition at the end of the free space, leaving out something like 10 gig (or more if you want) of free space for Ubuntu on the left side of the GUI  (beginning of drive) then boot from the Ubuntu install CD and install on the free space left on hdb.
I suggest having a big  partition with FAT32 on both hdd because the OSes dont need more than 10 GB each and the rest is file storage that you can have on FAT32 for easy access, but if you have much data on your old drive, maybe you want to make some room, move some data and so on before you partition that drive too; you can keep NTFS to begin with, Ubuntu can read it easly (but it is generally raccomended NOT TO TRY writing on NTFS with Linux)
Oh, yeah, and when you get to the Grub part (that's the Boot loader) install that in MBR (the default option) it wont work on multiple hdd's if you install it somewhere else.

---

### Post by tico on 2006-01-23
To Luke771:

Thanks for the suggestion, but I'm using a notebook and it's almost impossible to add a HD (too expensive for me :(  ).

To all:

What's te minimum amount of space to make o good Ubuntu configuration?

---

### Post by Luke771 on 2006-01-23
I have it up and running on 6 Gb plus 2,2 of Swap space (swap partition is proportional to your RAM memory; I have 512MB so I need 2,2 Gig (ubuntu takes care of this)
I guess it can work on a 3GB partition plus swap space, if you dont plan to install lots of massive programs in it, and you still need some file storage space if you don't have a fat32 partition whaere you can store files under both OSes, but anyways, as long as we just talk about to make it work, 3Gb+Swapspace should do, (but I still would reccomand at least 6GB plus swap) 10Gb + swap give you some extra space untill you make some room and make a new both-os-partition.
hmmm I didn't know that notebook hdd were particularly expensive, but I don't know anything about notebooks... anyway, that's another reason to stick with regular old fashioned machines, big, heavy, with lots of cables, but cheap and easly uppgradeable.

OK then, all you need is about 12 GB of free space, then install Ubuntu in the free space and install Grub on hd0,1 
that means on the second partition of the first hard drive (the count starts at zero not at 1)that way you wont modify the master boot record (MBR), so if you want do go back to windows (and why the hell would you?!?) all you need to do is to delete the Linux partition and allt will be back as it was before; if you istall Grub in the MBR and want to go back to windows you will have to restore the MBR after deleting the Linux partition, to do that you use the windows install CD in rescue mode and run fixmbr
(well, if I remember right, but you wont need that... more probably you will stick with linux for the rest of your life)

---

### Post by Robor on 2006-01-23
I'm dual booting Ubuntu 5.10 and WinXP Pro on my IBM T42.  My Windows partition was already installed using NTFS as the file format so what I did is this...

1)  Chkdsk and defrag from Windows
2)  Boot with Ubuntu CD and repartition (I split my 60GB drive in 1/2)
.....a)  Windows got 1/2 (30GB) of the drive
.....b)  Linux got the other 1/2
..........1.  Root ( / ) got 10GB
..........2.  Home ( /home ) got 14GB
..........3.  Swap (no mount point) got 1GB
..........4.  I used the rest ( ~ 5GB) for a vfat partition so Windows and Ubuntu could read and write to it.
3)  Installed Grub into the first partition replacing the Windows loader
4)  Followed the easy install process
5)  Verified Linux and Windows could both boot and read/write to the FAT partition.
6)  Configure Ubuntu

To answer your question about booting Ubuntu/Windows.  I've had Ubuntu on my laptop for about 6 weeks and I've booted Windows only to patch it.  :)

---

