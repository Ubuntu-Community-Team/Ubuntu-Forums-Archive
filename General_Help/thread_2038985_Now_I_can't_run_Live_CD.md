---
title: "Now I can't run Live CD"
date: 2012-08-07
forum: General Help
---

### Post by Abbydabs on 2012-08-07
I installed Lubuntu (latest version) onto a SCSI 36 gig HD with 4 gigs of RAM.  I'm using it now and simply love it!   My problem is ...now I want to try my hand at partitioning.    I want to make resize the HD and make another partition of 18 gigs for storage.   I know I have to run Gparted from Live CD to do it but now I can't.   The CD drive fires up and the menu appears to run Live CD, install Lubuntu, check disk for errors etc.   I choose Live CD.   After a minute or so with a blinking cursor, error messages appear saying "timeout 228" and keep running down the screen forever.     I know the CD is good as it works on my laptop.    Plus, I have several other distros (Puppy, PCLOS, Mint etc.) and now I can't run Live CD with any of them either since I installed Lubuntu on this machine.   Lubuntu is running just fine with no problems so far.    Any thoughts as to why I can no longer run Live CD?

---

### Post by Rex Bouwense on 2012-08-07
Try cleaning your CD drive, especially since none of your CDs can boot.  Can you use the CD drive otherwise?

---

### Post by Abbydabs on 2012-08-07
I ran a CD cleaning disk and tried again with no success.  The drive must be working as I tried a Win XP CD and it got to where you choose where to install the OS.  This computer I have is a server with two Xeon 3.06 CPU's.   It had 8 SCSI drives with two RAID controllers and two IDE drives.  I'm using a RAID controller with one SCSI drive.   It took me a while to get it going as I never had any experience with SCSI.   I'm going to uninstall the hard drive I'm using now and install one of the other seven and try an install on it.  Don't know what else to try.  Maybe another CD/DVD drive?   I have lots of them.

---

### Post by 2F4U on 2012-08-08
Do you have the option to boot from a usb flash drive? If yes, you can create a live usb out of your running Lubuntu installation:

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)

---

### Post by mastablasta on 2012-08-08
> **Abbydabs said:**
> I ran a CD cleaning disk and tried again with no success. The drive must be working as I tried a Win XP CD and it got to where you choose where to install the OS. .
 
 
that's no indication.
 
i just had to place a drive that wouldn't read DVD-R anymore but would hapilly read all CD and DVD+R

---

### Post by jemadux on 2012-08-08
have you tried to make LiveUSB ? 

also dont make to many formats on your hdd drive cuz somewhere will not run

---

### Post by Abbydabs on 2012-08-08
No, I haven't tried going Live USB ..yet, but I have been messing around with partitioning.   I didn't think about formatting maybe causing a problem.   I'm trying to learn Linux partitioning with GParted and I attempted to take the 36 gig drive and resize it down to 18 gigs and make a new partition of unallocated 18 gigs for storage.   It didn't work.  I remember deleting  what I thought was the second partition (sda3) not using Live CD.  I'm going to try installing Lubuntu on another drive (I have 8 of them (SCSI's)) right now and see what happens.  I'll be back shortly.   Thanks guys.

---

### Post by Abbydabs on 2012-08-08
Well, it took a while but I found the problem.  It was a bad stick of RAM.   I didn't consider that as Lubuntu was working just fine.   But I began thinking that Live CD loads and runs in RAM so why not test the RAM.  I did and found errors on one stick.   Took it out.  Now using just 3 gigs and Live CD now works.   Now I have to learn Linux partitioning.   My thanks to all that helped.

---

