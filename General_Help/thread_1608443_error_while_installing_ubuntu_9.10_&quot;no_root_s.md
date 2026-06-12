---
title: "error while installing ubuntu 9.10 &quot;no root system defined&quot;"
date: 2010-10-29
forum: General Help
---

### Post by vat with tux on 2010-10-29
Hi friends!
I'm currently having windows7 on my machine.I tried installing ubuntu 9.10 from it's disk image by mounting it using winmount.I choosed the option "install inside window". After some process it asks to reboot pc to continue installation. After rebooting i choose ubuntu from the boot menu. Then after some time it shows an error saying something like "no root system defined please correct this from the partitioner". Then pressing ok or cancel the same message appears again & again. So i have to restart my pc using hardware button.This is the problem.
So please someone help me to resolve this problem. Thanking in advance.

---

### Post by Rubi1200 on 2010-10-29
Hi and welcome to the forums :)

There are basically 2 options available for installing Ubuntu:

1. using Wubi: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
This creates a virtual version of Ubuntu **inside** your Windows installation.

2. burn the image to a CD and install from the CD to the hard-drive: 
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

The problem you describe may occur as a result of already having 4 primary partitions (the maximum allowed).

Please tell us how your drive is currently partitioned (include a screenshot if you can).

Thanks.

---

### Post by vat with tux on 2010-10-30
Hi! I'm having six partitions in my windows 7. I've attached screenshot of windows disk management.I've also attached screenshot of my computer. Please check it out & suggest something.:)

---

### Post by joshruehlig on 2010-10-30
Honestly I suggest a regular install of ubuntu (either 10.10 or 10.04). I have heard many bad thing about installs inside windows, but I may be wrong. 
If I were you I would create a ubuntu cd / usb.
Boot into it and change partition off space with gparted.
And finally install into that space created (Minimum 4GB)

Looks like your pictures HDD has enough space but it may get cramped... U may want to move files around a bit too tidy up space for ubuntu

---

### Post by Rubi1200 on 2010-10-30
Ubuntu can be happily installed to a logical partition, but you need to create space for it; at least 10GB is recommended.

Also, if you are using Windows 7, please do your partitioning from within Windows using the Disk Management tools. Then, reboot a few times to make sure Windows is happy or if it needs to run chkdsk, let it do so.

Then install Ubuntu to the space you want using the CD.

[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by vat with tux on 2010-11-06
Actually i was busy in festivals.:) that's why responding too late. 
But i have tried very hard to install ubuntu inside windows. But same problem continues. Also i would like to tell that previously i have also tried to install ubuntu using cd but at that time when partitioner window opened at that time it was not showing current partitions rather than that it was showing my whole 160 gb harddisk as empty & a single partition. Below that there was written that "currently no operating system is installed on this pc." But actually i was having windows 7 installed at that time. 
So if still any ways to install ubuntu inside windows then please suggest if possible i want to install ubuntu using wubi installer.:)
Thank u.:)

---

### Post by brian_milnes on 2011-05-06
I have a little old Windows PC.
 
Can run Live CD fine 9.10 or 10.10
 
Both can see the hard disk
 
I have used GParted to partition and format the drive successfully.
 
However, with both versions, I get to the setup partition menu and it is empty. When I click forward it comes up with error "no root system defined" edit in Partitioner.
 
But that has no option (all are greyed out).
 
Anybody care to cast useful information, please?
 
Thanks
 
Brian

---

