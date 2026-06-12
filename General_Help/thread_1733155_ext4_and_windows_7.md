---
title: "ext4 and windows 7?"
date: 2011-04-18
forum: General Help
---

### Post by cbennett a7xftw on 2011-04-18
well i want to install windows 7 over ubuntu on my buddys computer and windows 7 wont go on the ext4 harddrive.. how do i fix this so i can install windows 7 on it. and it dosnt give me the option to format the drive from the setup of windows 7..
and gpatred isnt doing anything for a partition..

---

### Post by marl30 on 2011-04-18
Use a live Ubuntu cd and use Gparted from the live cd to format the hard drive to NTFS. You should be able to install Windows 7 without a problem afterwards.

---

### Post by cbennett a7xftw on 2011-04-18
> **marl30 said:**
> Use a live Ubuntu cd and use Gparted from the live cd to format the hard drive to NTFS. You should be able to install Windows 7 without a problem afterwards.

hmm ok ill try

---

### Post by wilee-nilee on 2011-04-19
Right click the swap if your resizing the ext partitions, and turn it off in gparted.

Build the ntfs with gparted right click it and then manage flags then boot, this make it active so the W7 install will recognize the partition. I f you do not build the ntfs ahead of time for installation you risk having other partitions go unallocated.

---

### Post by Mark Phelps on 2011-04-19
Best NOT to use GParted to create the partition.

Instead, leave the space unallocated and allow Win 7 to do the formatting as part of the install.

---

### Post by dragonfly41 on 2011-04-19
And after you have installed windows 7 ....

create a system restore point

create a recovery disk

download and install EasyBCD

[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

create two boot entries using EasyBCD

One already under Windows tab
another under Linux/BSD tab .. pointing to your ext4 Ubuntu partition


I've just gone through this process with Vista on one ntfs partition .. Ubuntu on another ext4

after startup repair .. 

bootrec /fixmbr
bootrec /fixboot

---

