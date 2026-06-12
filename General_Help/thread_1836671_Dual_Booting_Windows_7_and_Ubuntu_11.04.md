---
title: "Dual Booting Windows 7 and Ubuntu 11.04"
date: 2011-08-31
forum: General Help
---

### Post by jag3498 on 2011-08-31
A few months ago I installed Ubuntu 11.04 on my ASUS EEE PC 900HA. I'm very happy with Ubuntu, but there are some thing that I need windows for. I Have a copy a windows 7 so i thought i would dual boot. I read the help guides on it and thought i would just recover the GRUB using boot-repar. So I backed up my files and using GParted, shrunk Ubuntu's partition and created a new NTFC partition. I then shutdown and booted from the windows 7 CD. I came to the point were I selected witch partition to install on. I selected the NTFC partition and clicked next. It gave me the following error: "Setup couldn't create a new system partition or couldn't find an existing one". I then Deleted it and created one using the installer. It still gave me the same message. I then shutdown and booted into Ubuntu. I deleted the partition to let it make its own. I created the new partition with the 7 installer and selected it. Same message. I know I could wipe out the drive, but I don't want to loose my settings or application.

Jack

---

### Post by oldfred on 2011-08-31
The first install of Windows has to be to a primary partition. Either you create a NTFS primary with the boot flag or have unallocated space with an available primary partition.

Have you used all 4 primary partitions?

---

### Post by jag3498 on 2011-08-31
I do not think I have used 4 primary partitions. The drive currently has 2 partitions with 70 GB of unallocated pace. After i create a partition there using the windows installation, select it and hit next it it gives me the same message:  "Setup couldn't create a new system partition or couldn't find an existing one". Should I create a NTFS partition in GParted and give it a boot flag?

---

### Post by Bucky Ball on 2011-08-31
It probably wants to be right at the start of the drive, first partition, hd0,0. Are the other partitions there (sda1, sda2, etc)? There are ways around that (you could move the two Ubuntu partitions and leave free space at the beginning of the drive, BUT, this might not change the was Win labels them (thus, the Win install will still see the first Ubuntu as sda1 (which is where Win wants to be) even though it's the second partition on the hard drive, if you follow me.

And as mentioned, must be a primary partition. It will add boot flag when installing, if you can get there, so wouldn't bother creating NTFS partition previous to install. Leave free space and let Win do it.

---

### Post by jag3498 on 2011-08-31
I moved them and, as you suggested windows still labeled them the same. I created a partition in the installation but it still has the same error.

---

### Post by Bucky Ball on 2011-08-31
Hmm, as I thought. Could be your problem. But I'm sure there's a way; MS couldn't be that anal.

Just sniffing around and it's a problem I don't see much out there. You'll need to repair the Ubuntu grub menu as installing Windows will wipe this (it writes to the MBR), this much I know.

How many partitions do you have on that drive? Primary? You have four already??? Or just the Ubuntu two? 

*** Here's the kicker, just discovered it. You can have a maximum of four; you would consider Windows 7 as one partition, BUT, and a very big but, Win7 install apparently creates an additional 100Mb recovery partition, so a Win7 install = 2 partitions. If you have three partitions on your disk already, you are trying to fit five with the Win7 install and computa says "no".

One last point: Check the Win7 system requirements. Are you leaving enough free space? Win7 needs a wide berth from memory, somewhere near 30Gb.

---

### Post by jag3498 on 2011-09-01
Here is a image of the disk in GParted. I moved the partitions back to the way they were since moving them had no effect on the installer. Oh, and I was going to use this:  [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
To repair the Grub menu.


[IMG]http://i52.tinypic.com/1z5q7i8.png[/IMG]

---

### Post by Bucky Ball on 2011-09-01
Yep, you have three partitions. sda1, 2 and 5. That is your problem. ;)

What I would do? Boot from the liveCD, open Gparted and kill sda2 (extended partition) and sda5 (/swap). You will need to kill sda5 first as it is inside the extended partition. Move sda1 so you have enough room for the Win7 partition at the front of the disk. Install Win7.

You should now have, in this order, Win7, Ubuntu, unallocated space. Boot from the LiveCD again. In the unallocated space now left behind the / partition create an extended partition and put the /swap back in there. Now Windows is installed you can put as many logical partitions inside the extended partition as you like. Three primary partitions plus and extended = 4 primary partitions, regardless of how many logical partitions are inside the extended.

Hope that all makes sense. Good luck with it.

---

### Post by jag3498 on 2011-09-01
It worked! I am now happily running a windows 7 and Ubuntu dual boot. Thanks so much guys!

---

### Post by Bucky Ball on 2011-09-02
Excellent news! No problem and enjoy the wonderful world of Ubuntu and Linux! ;)

---

