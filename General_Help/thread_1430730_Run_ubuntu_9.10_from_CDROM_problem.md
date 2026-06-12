---
title: "Run ubuntu 9.10 from CDROM problem"
date: 2010-03-15
forum: General Help
---

### Post by neil0mac on 2010-03-15
I have a number of problems, actually, but don't know where to start i.e. which one to fix first!

1.   On a 64 bit AMD PC running RAID 1 setup which has a broken arrray (the source disk is the problem, I think).  Since I have started to run Ubuntu, I am no longer able to remove the CD from the drive - even using the manual eject with a paper clip when the PC is turned off.

2.   Is there a thread for the problem trouble shooting of Raid issues on Ububtu forums.    My searches suggest that there aren't any.

3.   I am running two Seagate Barracuda 80GB HDDs.    Sometimes they show around 74GB sizes and sometimes 52GB sizes.  

I Couldn't remember if I set them up (a year or so ago) on two partitions or one.    Having just found the partition tab in Ubuntu and used it, i Get ...

/dev/sda -Gparted   (74.53GB)
.... /dev/sda1 (with an exclamation mark)... ntfs ..................48.83 GB ....  boot
  unallocated                                           unallocated ...........  25.7 GB(With no flag)

What does the exclamation mark signify for this HDD?

/dev/sdb -Gparted   (74.53GB)
.... /dev/sda1 (with an exclamation mark)... ntfs  ..................48.83 GB ....  boot
  unallocated                                           unallocated  ...........  25.7 GB(With no flag)

And. What does the exclamation mark signify for this HDD?


/dev/sdc -Gparted   (74.53GB)
  unallocated                                           unallocated  ...........  74.5GB  (With no flag)

Looking further, I think I remember setting up the first partition at 50GB - which would equate to 48.83 GB of usable space?

AM I right in assuming that the "/dev/sdc" is the new HHD substitution for the mirror HDD?   (I am trying to preserve all d ata in the system as it is a collection over many yers and is irreplaceable.)


The original RAID setup was for WinXp using VIA Raid 8327 but I doubt that that makes any difference.

4.   For the last 2 days, the source disk appears to  be readable, but when I ask it to duplicate to a (third) new Seagate Barracuda 80GB HDD, I get an error message that it can't be done.

I have the option to 'Destroy the Array" - but what  does that do?  Erase both HDDs?  Or simply break the linkage between the soruce and mirror HDDs?

---

### Post by dcstar on 2010-03-15
> **neil0mac said:**
> I have a number of problems, actually, but don't know where to start i.e. which one to fix first!

1.   On a 64 bit AMD PC running RAID 1 setup which has a broken arrray (the source disk is the problem, I think).  Since I have started to run Ubuntu, I am no longer able to remove the CD from the drive - even using the manual eject with a paper clip when the PC is turned off.
........

If you cannot get a CD-ROM drive to eject after boot-up - and before Ubuntu loads - then you have a hardware problem, not an Ubuntu problem.

---

### Post by neil0mac on 2010-03-16
> **dcstar said:**
> If you cannot get a CD-ROM drive to eject after boot-up - and before Ubuntu loads - then you have a hardware problem, not an Ubuntu problem.
  
Solved that one by 'Adding a file' (well, actually, using a file - to reduce the height at the  'front' of the two small lugs, by more than half, to make placing the CD in the right position.   I didn't occur to me that there might  be a physical obstruction to the eject process, but when I thought about it, I could hear the drive try to eject the CD, and close the draw again when it couldn't.

One problem solved - only about 3 or 4 more to go!


Thanks.

---

