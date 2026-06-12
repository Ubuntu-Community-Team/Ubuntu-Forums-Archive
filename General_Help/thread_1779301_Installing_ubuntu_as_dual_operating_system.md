---
title: "Installing ubuntu as dual operating system"
date: 2011-06-10
forum: General Help
---

### Post by ikirby77 on 2011-06-10
Hi all,

I am trying to install ubuntu as a dual operating system with windows 7. I am a little bit confused as to what I should do in the allocate drive space section. I have a table displayed as follows:

Device size used

/dev/sda1 208 mb 69mb
/dev/sda2 485491mb 80607mb
/dev /sda3 14297mb 11916mb
/dev/sda4 108mb 33mb

I then have another drop down menu with the header: Device for boot loader installation. Menu options:

/dev/sda ATA TOSHIBA MK5056GS(500.1 GB)
/dev/sda1 Windows 7(loader)
/dev/sda2 windows recovery eniroment (loader)
/dev/sda3 windows recovery eniroment (loader)
/dev/sda4

I am very new to ubuntu and hard drive partitioning, I would be very grateful if someone could give me some advise on the options I should select before clicking the install now icon.

Thanks

Ian

---

### Post by ChipOManiac on 2011-06-10
Why don't you try the "Install along my current operating system"... you can graphically specify the size...

---

### Post by ikirby77 on 2011-06-10
Hi,
 
For some reason when I try to install Ubuntu, the allocate drive space window only gives my two options:
 
1. Replace windows 7
2.Something else
 
I believe you are normally given 4 options, is there a reason why I am only given 2 options??
 
Thanks
 
Ian

---

### Post by Mark Phelps on 2011-06-10
You're only given those options because it looks like you already have the limit of 4 primary partitions -- thus, the installer is unable to create any more partitions.

Also, do NOT try to force the installation -- that will end up converting your Win7 partitions to Dynamic Disks -- presenting you with a whole new set of problems you don't want to have to deal with.

Also, BEFORE you do anything else, go into the Win7 Backup feature and create and burn a Win7 Repair CD.  You will need this later if any problems develop during the dual-boot installation to repair the Win7 boot loader.

And finally, do NOT allow the Ubuntu installer to shrink the Win7 OS partition to make room for Ubuntu.  Doing so risks corrupting the Win7 filesystem and rendering it unbootable.

---

