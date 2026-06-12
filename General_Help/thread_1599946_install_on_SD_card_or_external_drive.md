---
title: "install on SD card or external drive"
date: 2010-10-18
forum: General Help
---

### Post by yamaha83 on 2010-10-18
i have done some searches on this and can only find stuff back in like 2005 and 2006. im wondering with an install of ubuntu onto an sd card (4-16gig) is worth it? is it just as fast as on the internal HDD? if its slower by how much? and also, what are the speeds like with ubuntu installed on an external HDD? the same as the internal? 
 
i would love to just have a full install on my laptop but need the use of photoshop cs5 and light room 3 and i only have 250gig HDD on my laptop and with all the photo work i do im not sure how much of that i can afford to give up to ubuntu... 
 
any advice on what would be best would be awesome! im running windows 7 if that helps. tried doing a dual boot sytem and it somehow took over the whole HDD... so good thing i backed up all the important stuff before i tried the install... 
 
one more question, witha dual boot system, are things like music and photos able to be accessed by both windows and ubuntu?

---

### Post by Lazaruss on 2010-10-18
At a guess, i'd say it might be marginally slower from an SD card, especially if it's a USB reader - same for other external devices. I'm not saying anything for whether it is possible...

I'd suggest putting the photos on an external device if you have one, and dual boot by partitioning the hard drive - 250gig is a lot of space...

When installing ubuntu, do manual partitioning to make sure it doesn't wipe the whole drive.

Ubuntu can access ntfs and fat32 drives usually very easily, but the reverse is a little harder... Windows can't access ext2/3/4 drives (standard for Ubuntu etc) without certain softare such as [diskinternals linux reader]("http://www.diskinternals.com/linux-reader/")

---

### Post by yamaha83 on 2010-10-18
i know its possible i have just heard that there may be speed issues with the sd card... i may just try and partition off like 50gig for ubuntu... is there a way to get to my music and videos and stuff that are saved through windows from ubuntu since they are on the same HDD? or does the partioning make that not possible? also, is there a way to edit the partion size downt he road without affecting data if say downt he road i want to give ubuntu more or less room on the hdd?

---

### Post by Lazaruss on 2010-10-18
ubuntu *should* be able to access the windows partition, but changing files may cause errors with permissions etc.

You can edit partitions later on, but it would be more likely that you lose data. You'd use something Like GParted (Gnome Partition Editor)

---

### Post by efflandt on 2010-10-18
Many laptops have a memory card slot that you cannot boot SD from.  But it will work from a USB card reader and the built-in card reader on both of my desktops are internally connected by USB.  So I can boot from SD on them.  I even have bootable live/install iso with persistent data on microSD.  But I don't have any SD larger than 2 GB (other than in my camera), so not sure how quick a regular installation is on SD.  But even the install iso on SD (with compressed file system) boots much quicker than CD.

I am currently running 64-bit 10.10 from a usb hard drive (WD Passport) which is more economical for the amount of space than flash memory.

sudo hdparm -t /dev/sda (internal SATA drive)
/dev/sda:
 Timing buffered disk reads:  354 MB in  3.01 seconds = 117.72 MB/sec

sudo hdparm -t /dev/sdf (usb hard drive, booted from)
/dev/sdf:
 Timing buffered disk reads:   98 MB in  3.04 seconds =  32.22 MB/sec

sudo hdparm -t /dev/sdg (microSD in old external Lexar usb SD reader)
/dev/sdg:
 Timing buffered disk reads:   24 MB in  3.18 seconds =   7.55 MB/sec

sudo hdparm -t /dev/sdb (same microSD in built-in usb SD reader)
/dev/sdb:
 Timing buffered disk reads:   38 MB in  3.01 seconds =  12.64 MB/sec

I don't have any SDHC to try.

---

### Post by Schrute Farms on 2010-10-18
Just to add my experiences to the thread.
I dual boot an old laptop between XP and Ubuntu 10.04.  It only has an 80Gb hard drive, so I gave 25Gig to Ubuntu & the rest to Windows.  After a year of regular use in Ubuntu, it's only used 15Gig, so if space is an issue (kinda funny for me to say about 250Gb), you don't need to give Ubuntu a lot of space.
Just remember to save anything you may need to access in Windows to the Windows partition.  I've never had any problems doing that.  Or, install a program that allows Windows to read Linux partitions.  (I've never tried one, so I can't say how well they work).

---

