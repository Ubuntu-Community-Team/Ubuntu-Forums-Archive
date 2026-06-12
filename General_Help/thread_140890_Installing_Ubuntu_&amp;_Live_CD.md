---
title: "Installing Ubuntu &amp; Live CD"
date: 2006-03-07
forum: General Help
---

### Post by MJyu on 2006-03-07
I'm going to install Ubuntu on my PC , running with WindowsXP as DualBoot
I was going to try Live CD prior to that , but it isn't working.
I set CD-rom as first boot device in BIOS and insert the Live Ubuntu CD , but I'm getting an error.Does it mean that the Install version won't work either.
Another question ,I've partitioned my hard disk in 3 partitions ( 2 for Win & 1 for Ubuntu) and it looks like this
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=6808&stc=1&d=1141726742[/IMG]

I would install Ubuntu on partition E and it's already formated in FAT32.Is it Ok or I have to reformated to ext format or Ubuntu will do it when Instalation is started

---

### Post by soonindallas on 2006-03-07
[QUOTE=MJyu]I'm going to install Ubuntu on my PC ... but it isn't working ... I'm getting an error[/QUOTE]

you're not giving enough info to answer this:

[QUOTE=MJyu]Does it mean that the Install version won't work either[/QUOTE]

What error are you getting ?  does the cd boot at all ?

Most failures to boot live cds are due to badly burned disks.

Check the md5sums with this windows utility [http://prdownloads.sourceforge.net/wxchecksums/wxChecksums-1.2.0-installer.exe?download](http://prdownloads.sourceforge.net/wxchecksums/wxChecksums-1.2.0-installer.exe?download)
and burn another disk  (try a slower speed) if the md5 sums don't match those you find in the dowload mirrors.


[QUOTE=MJyu]Another question ,I've partitioned my hard disk in 3 partitions ( 2 for Win & 1 for Ubuntu) and it looks like this
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=6808&stc=1&d=1141726742[/IMG]

I would install Ubuntu on partition E and it's already formated in FAT32.Is it Ok or I have to reformated to ext format or Ubuntu will do it when Instalation is started[/QUOTE]

Can't see your pic, but you will need to reformat the partition with a linux filesystem.  If you're sure there's no data you need on this partition, accept the installer's prompt to reformat it when you do your install. You will also need a swap partition. The simplest for you would be to choose "guided partitioning" when you get to this stage with your install disk.

---

### Post by justleen on 2006-03-07
It would be good to post the error you are getting on the live CD..

On the formating bit, you can leave it at fat32 the setup will do the formating to ext3 for you, personally i find it easier to simply delete the partition in windows and install ubuntu on the free space (the setup has a nifty option to only use the free space)

---

### Post by MJyu on 2006-03-07
I've tried all 5 CDs from the original Ubuntu pack  having the same problem
'cause I couldn't do the Screen shot , I wrote down the error message
> **Kernel panic-not syncing:Attempted to kill init**

> Check the md5sums with this windows utility [http://prdownloads.sourceforge.net/w...r.exe?download](http://prdownloads.sourceforge.net/w...r.exe?download)
[[IMG]http://img106.imageshack.us/img106/1185/ch0tw.jpg[/IMG]](http://imageshack.us)

Seems OK to me
---------------------------------------------------------------------------
> i find it easier to simply delete the partition in windows and install ubuntu on the free space (the setup has a nifty option to only use the free
Like this:) 
[[IMG]http://img69.imageshack.us/img69/7350/part2kt.jpg[/IMG]](http://imageshack.us)

---

### Post by SWAT on 2006-03-07
I would still try to install Breezy on your PC, and use your PC as dualboot. There is a wiki-page about WindowsDualboot :D

---

### Post by soonindallas on 2006-03-07
check your ram.

[http://www.ubuntuforums.org/showthread.php?t=135920&highlight=kernel+panic+kill+init](http://www.ubuntuforums.org/showthread.php?t=135920&highlight=kernel+panic+kill+init)
[http://www.ubuntuforums.org/showthread.php?t=83156&highlight=kernel+panic+kill+init](http://www.ubuntuforums.org/showthread.php?t=83156&highlight=kernel+panic+kill+init)

---

### Post by justleen on 2006-03-07
[QUOTE=MJyu]

Like this:) 
[/QUOTE]
Exactly like that, yes :)

---

### Post by MJyu on 2006-03-07
I've just recently checked my RAM (2x256MB) due to some problems with Windows.I run everything I've found ( GoldMemory , MemTest etc)and they have found nothing.
Are there any Linux specialized apps that I could try?:-k 
This guy
[http://www.ubuntuforums.org/showpost.php?p=475379&postcount=5](http://www.ubuntuforums.org/showpost.php?p=475379&postcount=5)
has mentioned some test from the install CD:???:

---

### Post by soonindallas on 2006-03-07
yep.  run memtest just like this guy.

---

### Post by MJyu on 2006-03-07
How to do that:confused: 
Do I have to run the Ubuntu install CD as a first boot device or to explore it from Windows?

---

### Post by soonindallas on 2006-03-07
you would boot from it.  put it in your cdrom drive, boot making sure the boot order in your bios put the cdrom drive before the HDD.

don't worry, ubuntu is not a virus.  you have to agree for it to install!

---

### Post by MJyu on 2006-03-07
It won't install:( 
Well , see you next time ( when I buy a new computer):)

---

