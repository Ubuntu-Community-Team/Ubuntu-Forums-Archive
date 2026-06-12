---
title: "clone a USB HD to another USB HD"
date: 2010-09-14
forum: General Help
---

### Post by three_jeeps on 2010-09-14
I have a HD that has an Ubuntu installation on it (30GB).  I want to clone this disk to another HD of slightly larger size (40BG).
My plan is to put each disk into its own usb enclosure.  I then want to boot a PC from the current version of Ubuntu Live CD and use 'dd' to do the the image copy. There are reasons that I want to do it this way, and not boot the 30gb hd that has ubuntu on it and copy it to the 40GB usb drive.
My question is: has anyone done this and does it work?  Any hickups along the way that I should know about?
I would use the approach documented here: [http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk](http://www.linux.com/learn/tutorials/8225-clone-your-ubuntu-installation-onto-a-new-hard-disk)
 
thanks for your insight..
John

---

### Post by C.S.Cameron on 2010-09-14
It works, I've done it many times.
```
sudo dd if=/dev/sda of=/dev/sdb
```

It may take some time,(hours), with a 30GB drive. There is no timer to tell you how things are going, don't be tempted to quit in the middle.

---

### Post by Grenage on 2010-09-14
Seconded.  I've done it before; just use gparted to expand the partition when done.

---

### Post by three_jeeps on 2010-09-14
> **Grenage said:**
> Seconded.  I've done it before; just use gparted to expand the partition when done.

I haven't used gparted before... but I have used barebones DOS tools as well as 2-3 versions of Partition Magic (both CL and GUI based).  I assume gparted is similar from what i've read....

I assume it will tell me that the last partition stops at sector (block?) xx and the unallocated space stops at sector (block?) yy, so I should use gparted to extend the last partition to sector yy??

thanks
J

---

### Post by Grenage on 2010-09-14
Gparted is a very self-explanatory program, with a great GUI.  It's installed by default on the LiveCD, but it can also be installed via apt-get or synaptic.  You can inspect partition start/end sectors, or just drag the partition on the GUI.

---

### Post by three_jeeps on 2010-09-14
Thank you...much appreciated.

---

### Post by C.S.Cameron on 2010-09-14
dd duplicates the drive, if it is 30GB the partition on the target drive will only be 30GB.
Gparted will allow you to expand the 30GB partition to 40GB or else create a second partition.
My attempts to expand an XP partition created using dd did not work so I created a second partition.

---

### Post by three_jeeps on 2010-11-06
> **C.S.Cameron said:**
> It works, I've done it many times.


Just to follow up...I tried it many times.  It did *not* work.
I formatted the target disk (ext3), checked for bad blocks, ran dd per your dd command, varied the transfer size, and other dd options.  Even tried the variant ddrescue. All failed. Failures ranged from dd hanging, completed with errors, completed w/o errors.  When no errors were reported, I looked at the disk with gparted and it would say it looked ok.  I removed the source disk and inserted the target disk into the host machine, would not boot....the best it ever did was begin to run the loader and it would hang forever.  
Finally decided I spent way to much time on this (probably a good 6-8 hrs) tried my luck with Clonzilla.  Worked like a charm.  Cloning was fast (about 45 mins for a 30gb drive).Booted up with no problem, and the server was functional in all aspects (apache, mail, mysql, ssh, etc.). Not one hickup.
Based on my experience, don't waste time with dd...use clonezilla.

---

