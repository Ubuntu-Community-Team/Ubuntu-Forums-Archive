---
title: "How do I remove Ubuntu and install windows again?"
date: 2011-12-17
forum: General Help
---

### Post by Obeilez on 2011-12-17
Hi,

I have had Ubuntu for a while now but I need Windows XP again for my hobby (producing/djing).
I've been googling (and messing with Gparted) all day and couldn't find how to format Ubuntu (since it's the only installed OS on my computer)
Whenever I try to install windows and boot the cd it sais "No valid partition availble".
I only have one partition which has Ubuntu on it, but I don't know how to format it so I can install Windows XP again.
It's really frustrating for me since I really need Windows XP.
So, does anyone know how to remove Ubuntu Completly, and install windows XP again? (Remember, it's the only OS I have installed).
I don't want dual OS, I only want Windows XP on my pc.

Thanks in advance!

---

### Post by 3Miro on 2011-12-17
First of all make sure to backup all important data from Ubuntu, since it will be lost.

Then from the Windows XP disk, there has to be a way to repartition the HDD. Every XP CD that I have seen has the option to create/remove partitions.

If you want to use Gparted, you cannot do it while Ubuntu is already running. You need to boot from a Ubuntu liveCD or liveUSB and then you can delete all partitions. Once you have deleted all of Ubuntu's partitions, XP should create its own.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by newcolt on 2011-12-17
I am not sure if this will work, but you can try it.
Use a live cd, go to use without installing mode. Go to partition manager and format a drive of your hard disk to NTFS. Backup the data in it before you do this. Then try booting using the windows xp live cd.

---

### Post by bigseb on 2011-12-17
Not sure if you did this but when you tried to install XP did you let it format the disc. Not even sure if that's possible, been ages since I even saw XP, let alone tried to install it.

Alternative: create a dual boot with both Ubuntu and XP. Use Gparted to create a partition for XP. Install XP. Then run Gparted from a liveCD to delete the Ubuntu partition and absorb the free space into the XP partition.

I'm sure some guys here might know more about this though. Good luck.

---

### Post by Obeilez on 2011-12-17
Ok, so I tried running Ubuntu from an USB stick.
I was able to format the drive to NTFS, but whenever I tried to install windows it still doesn't find a partition for some reason.
Any ideas?

---

### Post by 3Miro on 2011-12-17
> **Obeilez said:**
> Ok, so I tried running Ubuntu from an USB stick.
I was able to format the drive to NTFS, but whenever I tried to install windows it still doesn't find a partition for some reason.
Any ideas?

At this point this really is a Windows issue, if you formatted your drive to NTFS, then Ubuntu is gone and Windows should be able to install just like it would on a machine that has never had an OS.

Did you try to go from within the Windows CD to delete all partitions and tell Windows to simply use all available space.

---

### Post by dyecide on 2011-12-17
Imo get a Windows 7 disc and use that to format the partition. Gparted might format it with wrong cluser size, which ancient XP can't handle.

---

### Post by thedarkdonut on 2011-12-17
Is the Windows XP install not reading your hard drive at all?  There should have been an option to do a new install as well as format the hard drive if the drive was detected.

---

### Post by Obeilez on 2011-12-17
It just can't find/create/delete any  partition.
The problem is I used to have vista home premium pre installed in a recovery partition but that got deleted with a Ubuntu install.
I tried finding the ISO on Microsoft website but I can't find it.
My dad had this XP CD so it's my only option.
I just don't know what I'm doing wrong...

---

### Post by thedarkdonut on 2011-12-17
Try this...

You must switch the SATA Mode (BIOS) to IDE from AHCI. 

Hit F2 at boot screen -> Main -> SATA Mode -> IDE 

This will allow Window XP to see your SATA.

---

### Post by xyzzyman on 2011-12-17
The reason XP can't see your hard drive is you have a SATA hard drive and XP doesn't know how to talk to SATA unless you remaster and burn a new CD with sata drivers on it, or if you're lucky your BIOS will have an option to make the SATA appear as IDE but then your performance will be much lower.

You can also use a USB floppy drive and floppy disk and put the sata drivers on there, and use F6 during XP install to install them like you would RAID drivers. Had to do that alot a few years ago when Vista came out and people wanted XP on their new laptops and desktops.

---

### Post by Obeilez on 2011-12-17
> **thedarkdonut said:**
> Try this...
 
You must switch the SATA Mode (BIOS) to IDE from AHCI. 
 
Hit F2 at boot screen -> Main -> SATA Mode -> IDE 
 
This will allow Window XP to see your SATA.
Thank you! Seems like it is working!
I'll keep you guys updated!

---

### Post by Obeilez on 2011-12-17
Ok, I installed windows xp, but I have an acer aspire 6530, which is my wireless driver, for wireless internet?

---

### Post by cottfcfan on 2011-12-17
The problem you may now have is, if you have just used a generic copy of XP, that isn't specific to your computer, you may well have to manually locate all the drivers for your hardware, (assuming they're available).
Happy googling, it took me an age last time I did that.

---

### Post by bigseb on 2011-12-18
> **cottfcfan said:**
> The problem you may now have is, if you have just used a generic copy of XP, that isn't specific to your computer, you may well have to manually locate all the drivers for your hardware, (assuming they're available).
Happy googling, it took me an age last time I did that.

^^ This

I also had an Acer laptop which came preinstalled with Vista. Took that off and put XP on and I also searched far and wide far drivers for all the different hardware components. I found out that many of the Vista drivers from my Vista backup disc also worked fine in XP so you may want to try that (hope you backed up :-k) .

---

### Post by Obeilez on 2011-12-18
I descided to stay with Ubuntu since it just won't work with Windows.
I enjoy Ubuntu alot, so I'll buy a Macbook Pro for my hobbies and keep using Ubuntu for personal usage.
Thank you all for the help!

---

