---
title: "Acronis True Image"
date: 2010-11-11
forum: General Help
---

### Post by w1ll1am on 2010-11-11
refreshed firefox at the wrong time sorry read post below

---

### Post by w1ll1am on 2010-11-11
Hello I would like to know if anyone had any advice on Acronis true image I am trying to figure out how it works and if there is a way to basically do the same thing in ubuntu but for free because thats really what its all about. so here are some questions I have.

-I read somewhere that acronis is a live CD and you can boot into it and then make an .iso of your hard drive is this true

-Can i use this on all of the computers i have including my windows computers? 

-is there any other way to do this in ubuntu?

-are there any other non free programs out there that others suggest ?

-I have /home on another HDD will it back up both and if so can i reinstall it on both or just one?

Thanks

---

### Post by uRock on 2010-11-11
Merged duplicate threads. Please only make one thread per subject.

Thanx,
uRock

---

### Post by |{urse on 2010-11-11
Yes to all your questions. Except the one about burning your hard disk to cd and booting from it, idk about that. Acronis runs on the linux kernel and copies images in a proprietary "true image" .tib file format. It can raw copy/write hard disks also. It works for windows and linux.

---

### Post by w1ll1am on 2010-11-11
> **|{urse said:**
> Yes to all your questions. Except the one about burning your hard disk to cd and booting from it, idk about that. Acronis runs on the linux kernel and copies images in a proprietary "true image" .tib file format. It can raw copy/write hard disks also. It works for windows and linux.

So you totally recommend it? Do you use it? Have you ever had it not work for any reason?

---

### Post by mike555 on 2010-11-11
Why not try Clonezilla ,it's free.

---

### Post by |{urse on 2010-11-11
Yeah I totally recommend it. There are also 5,000 other solutions taht do the same thing that I also recommend. I would recommend Acronis to a beginner and i would recommend creating a custom livecd with a simple startup script using genisofs and partimage. I would recommend that an advanced user, that's what I generally use.

So far as problems with acronis, my only complaint is that will not write to a raid5 while it is rebuilding, mine does that.

---

### Post by w1ll1am on 2010-11-14
Thanks for the replies I will try both ideas clonezilla looks cool and I like the broadcast and multicast features. thanks for the help. I am also trying Acronis I downloaded it from a torrent just to try and when i try to back up my ext4 ubuntu drive it says there are file system errors. It also will not let me save to an Ext4 partition I have to same it to a portable HDD that i had. Any thoughts?

---

### Post by efflandt on 2010-11-15
Acronis will work in some cases when clonezilla does not.  The problem with clonezilla is that although it uses compression for the image, it tries to read everything sector by sector.  While that makes it easy to image without knowing anything about the OS, it stumbles (errors and stops) on a drive with bad sectors that cannot be read.

Acronis can do sector by sector as an option, but its default is to just read from a partition what it needs to (which works better for a bad hard drive).  So as long as you have repaired your file system to not use bad sectors, it will work where clonzilla will fail.  I used the WD version of Acronis to image a bad drive, and it worked great on the warranty replacement.  In that case it was WinXP that refused to boot, so I used a USB enclosure to chkdsk /f it from another WinXP computer,  made sure the laptop could boot from it, then used USB enclosure to image it to a file which I used later to image the replacement drive.

I did not try the bootable image with Acronis because the laptop with failing drive does not have a DVD writer (just reader).

For some reason the Seagate version of Acronis will not run in 64-bit Win7 (which has a Seagate drive).

Does anyone know of a Linux disk imaging program that will work on a drive with bad sectors that have been locked out?  That is essential for a failing drive.

---

### Post by Mike_tn on 2011-01-10
> **efflandt said:**
> For some reason the Seagate version of Acronis will not run in 64-bit Win7 (which has a Seagate drive).
this part is confusing. what is a "*Seagate version* of Acronis"?

---

### Post by binoplaza on 2011-01-10
Dump acronis and use clonezilla, had myself a lot of issues with acronis while clonezilla worked from the first time like a charm and did exactly what it needed to do ...

I used it to duplicate an ext4 partition as well

---

### Post by efflandt on 2011-01-10
> **Mike_tn said:**
> this part is confusing. what is a "*Seagate version* of Acronis"?

Western Digital and Seagate have their own free version of Acronis, but those free versions are specifically for that manufacturer's drives I think.  So the WD version will image a WD drive and Seagate version would image Seagate or Maxtor drives.  But maybe you just have to have one of their drives on your system.

As I mentioned, Acronis worked to image a WinXP partition with bad sectors because it had a mode to just copy the parts with valid files, while clonezilla would throw up its hands and quit at the bad sectors because it would only do a sector by sector image and could not read those sectors (unless it had some option I overlooked).

---

### Post by w1ll1am on 2011-01-11
> **Mike_tn said:**
> this part is confusing. what is a "*Seagate version* of Acronis"?

I think it is like a preinstalled acronis that is used to make like recovery partitions on all new computers but I am not sure.

---

### Post by Mike_tn on 2012-04-11
> **efflandt said:**
> Western Digital and Seagate have their own free version of Acronis, but those free versions are specifically for that manufacturer's drives I think.  So the WD version will image a WD drive and Seagate version would image Seagate or Maxtor drives.  But maybe you just have to have one of their drives on your system.

As I mentioned, Acronis worked to image a WinXP partition with bad sectors because it had a mode to just copy the parts with valid files, while clonezilla would throw up its hands and quit at the bad sectors because it would only do a sector by sector image and could not read those sectors (unless it had some option I overlooked).

> **w1ll1am said:**
> I think it is like a preinstalled acronis that is used to make like recovery partitions on all new computers but I am not sure.

This reply is a little long in between posts. Anyway, thank you for the replies efflandt & w1ll1am. I use both Seagate external drives and Acronis so it got my curiosity. I vaguely recall looking into Acronis originally because of it's association with Seagate but never used the "Seagate Version".

w1ll1am, and to whomever reads this thread
ext* file systems are supported by Acronis TIH (True Image Home) with compression for full partition image backups. It works very well and is easy to use as the poster l{urse said. However full support is only for MS Windows. It needs to be installed on Windows to get the best functionality. A boot disk can be used but you may need to fuss that boot ISO with the Acronis staff after you buy True Image Home in order to get it to boot your machine if the hardware is newer. Acronis is extremely helpful and fast about doing so. I think it is money well spent. They use Acronis TIH at the Best Buy service desk near me to backup computers before doing work on them and I found a copy of the tech's version inadvertently put out on the sale floor and it was half price!  I was blessed. 

It is best to backup with Acronis TIH installed on MS Windows because it is known that a functioning TIH boot disc may not recover the saved backup file back onto the original location although installed Acronis will do it. As for specifics on Linux filesystems.  Older versions of Acronis TIH, like mine which is 2010, will do full partition backup of ext3 file systems and older filesystems like ext2. Newer versions, TIH 2011 and 2012 will backup ext4 filesystems. Since Acronis is Windows oriented, the software does not include backing up isolated Linux folders.

That said. I think it's the coolest backup system for Linux since sliced bread. I just install Linux onto ext3 for use with my TIH 2010. What does it do? You can make a backup, delete the partitions, remake them to different sizes, then lay it down. You can dig through your partition save for files and pull one out at anytime, just like rooting through any archive.

---

### Post by Mike_tn on 2012-05-01
**Addendum**: After more experimentation I found some good news for Linux users. That includes making a correction to what I wrote above;

> *It is best to backup with Acronis TIH installed on MS Windows because it  is known that a functioning TIH boot disc may not recover the saved  backup file back onto the original location although installed Acronis  will do it.***That quote is NOT completely true! **

I found you can use the bootable Acronis True Image Home ISO to *reliably* recover full partition images of Linux systems or recover images of your entire HDD and thus use this tool and still kick MS Windows out of your life entirely if you like. Here's how; If the bootable Acronis TIH ISO disk does indeed boot your hardware then it will recover any ext* filesystem it saved as long as the image to be recovered is residing on the Hard Disk it will be recovering onto.   (TIH reads ext3 partitions when using TrueImageHome2010 version, and ext3 or ext4 partitions when using newer TIH software versions) That means you need a partition to put the saved compressed image file you are recovering and a different partition to recover it onto, both locations must be on the same Hard Disk. 

So the good news is you do not need to install Acronis onto a Windows system to use it reliably for Linux. Don't forget, the Bootable Acronis ISO needs to be able to boot your machine in the first place but if you bought the software and have trouble with that part, the company will work with you quickly to get it booting. Where it does not work is when you try to restore a saved linux image through a USB port, from an external hard drive. That method did not work for me. I also recommend using a wired mouse for the procedure.

Thought this was useful because I read several posts of people wanting something similar to what Clonezilla tries to do making full partition images. Acronis may be more reliable, easier to use, and does not demand any Windows installations either.

---

