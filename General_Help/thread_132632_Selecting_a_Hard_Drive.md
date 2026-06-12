---
title: "Selecting a Hard Drive"
date: 2006-02-18
forum: General Help
---

### Post by simoncoul on 2006-02-18
I really want to make a complete switch from windows, but a few of the programs I need for school only run on windows.    Now I noticed when I hook up my ipod to linux and windows I can access the files on it from either OS.   

Is it possible to get a hard drive setup so I can access the files from both OS, such as music, movies, and pictures?  

Also if it is possible what would be better to use IDE or SATA.   I currently have a 120gb IDE drive but I do have connections for 4 SATA on my motherboard.

Lastly I'm gonna reinstall both OS if this idea is possible, which drive should I use to store my files and which one should have the OS's?

Thanks

Coulson

---

### Post by cilynx on 2006-02-18
If you are going to have shared data between Windows and Linux, you want to use vfat a.k.a. fat32.  The reasoning is that Linux can't write NTFS and Windows can't do anything with ext2/3 (which isn't completely true, but may as well be).

The media for your shared drive doesn't really matter.  IDE, SATA, USB External, whatever.  Personally, I have one SATA and one IDE in my main machine.  I don't notice any performance difference in the real world although the benchmarks of the SATA are better.  I do like the lack of cable clutter with SATA though.  You may run into troubles if you want to boot off of a SATA drive.

In all honesty, you could easily do the whole install on that one drive.  Maybe 30G for Linux, 30G for Windows, 60G for shared data.  I wouldn't think you would run into any problems on a setup like that.

Good Luck

---

### Post by simoncoul on 2006-02-18
Thanks cilynx.
Well I mess around with my computer alot and I'd like to have my files in a safe place so that they do not get corrupted... again... lol.

I was curious about why I may have problems if I try to boot off of a SATA drive?

And I have partition magic would I just use that to format one of the drives into fat32 format?

Also how big of a swap should I use when reinstalling ubuntu, I currently just used the default setting, I have a giga of ram and an amd 3500.

Thanks for the help

---

### Post by Ocxic on 2006-02-18
most computer bios won't or will have difficulty booting from SATA drives scince it's such a new technology, mine won't and I've tried. I also don't see a performance difference with either drive. 

As for your swap space, with that much ram, I doub't you'll even need it, i have 1GB of ram in my comp, and I don't even have a swap partition, i noticed that my machien would never use it even though I had one, so when i found out i caould get rid of my swap, i did and got my 2.5 GB back, YAY.

---

### Post by cilynx on 2006-02-18
As for data safety, short of total hardware failure, a separate partition is just as safe as a separate disc.  You can nuke both the Windows and the Linux partition and the data partition would still be safe.  You'd just have to reinstall something and then mount said partition as it was before.  (That sounds more confusing than it really is.)

I don't really know why SATA doesn't always like to boot.  I have a Genuine Intel mobo and it always craps out if I set it to boot the SATA drive.  As of now, I have Linux installed on the SATA drive and XP Pro on the IDE drive.  BIOS is set to boot the IDE drive.  I have Grub installed on the MBR of the IDE drive.  Thus, it appears that I boot the SATA by default, but I really don't.

On a personal note: avoid Partition Magic.  I've seen it eat way too much data.  If you need to splice and dice living partitions, check out 'gparted'.  Gparted is included on the Ubuntu 5.10 Live CD if you need to work on the disc you would normally boot.

For the sake of argument, let's assume that you're cutting your current drive in half and getting a new drive for data storage:

Set up the OS partitions whatever size you want.  Preferably, use gparted for this.  For the sake of argument, hda1 will be 59G for Linux, hda2 will be 1G swap, hda3 will be 60G for Windows.  Do not format / partition / set up the new drive.  You don't want Windows detecting it yet.

Install Windows.  The Windows installer should detect the windows partition and install on it.  It will also take over the MBR so that you boot Windows by default with no options otherwise.  (Which is why we install it first)

Install Ubuntu on the partition you set up for it.  Don't forget the 1G swap.  (I tend to use 1G on all modern systems.  I almost never see more than 10% usage of it, but a reasonably large swap partition can keep a system alive long enough for you to hunt down a memory leak after you notice it.)

The Ubuntu installer partitioner should give you the opportunity to mess with your new drive as well.  Make one partition that takes up the whole drive and make it Fat32.  Mount it somewhere like /media/shared/ or whatever you like.

The Grub installation inside of the Ubuntu installer should detect the Windows setup and put together the boot loader accordingly.

Hope this helps...

---

### Post by simoncoul on 2006-02-18
Alrite thanks everyone for the help I think I figured out what to do.

I'm gonna get a SATA drive and format it with a fat32 format, then transfer all my data(music and stuff) to it.   Take my current drive and erase the whole thing.

Install windows onto it but just 40gb of it.
Then install ubuntu onto another 40gb part with a 1gb swap.
Then save the last part just incase I install vista sometime if it ever comes out lol.

Thanks again everyone.

---

