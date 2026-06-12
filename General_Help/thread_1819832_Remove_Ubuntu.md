---
title: "Remove Ubuntu"
date: 2011-08-06
forum: General Help
---

### Post by blizzard1563 on 2011-08-06
I have a laptop that I am going to give my daughter for college. This laptop was salvaged from a friend who was going to trash it. It needed a new hard drive. So after installing the hard drive, I installed Ubuntu. Now that my daughter is going to use it for school I need to put windows on it. I have a Windows XP CD. When I go to start it up with the windows disk, it starts the windows install but then stops and states that the computer does not have any disk drive disks and f3 to exit windows set up.... when i reboot the computer with out the windows disk, Ubuntu loads up fine and no problems. I need windows for the software she is going to run. Any help would be great. Thank you in advance.

---

### Post by daccount10 on 2011-08-06
You should be able to repartition with the Windows disk. You could also try redoing the disk with the live cd. Also, if all else fails you might be able to find alternative software or run it on wine.

---

### Post by Alwimo on 2011-08-06
You have to reformat the hard drive to make it NTFS.

GNOME Partition Editor, GPartEd, can do that. You just download it and then burn the iso to a CD, then restart your computer while the disc is in it. You then follow the instructions to get into it. A window will then appear to let you reformat the various partitions you may have, and change their format. You want it to be NTFS in order for Windows to like it.

It can be downloaded here: [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by maxar6 on 2011-08-06
What you could do is install wine in ubuntu and wine allows you to install and/or run most windows programs. If you have any questions about wine let me know!

---

### Post by blizzard1563 on 2011-08-06
I tried a live CD and it just wanted to install Ubuntu in a second partition. It wont even give me that option with the windows CD. Some how i need to get windows on the computer. I don't have a problem keeping Ubuntu but i do not know how to make a new partition for windows

---

### Post by walt.smith1960 on 2011-08-06
Another option would be to dual-boot.  I too have software that only works with Windows.  I have several partitions and a boot manager.  I SEVERELY restrict Windows' access to the internet.  95% of my online work is done with various flavors of Linux.  I don't know if this would be an option or not. There is also a virtual machine option but that takes a fairly powerful machine I think.

---

### Post by maxar6 on 2011-08-06
Go to System > Administration > Disk Utility and see if you have any unpartitoned space. If you do then set that partiton up as NTSF and there you have a partiton for it. If you do not have any free space then you will have to wipe the whole drive and then install windows.

---

### Post by daccount10 on 2011-08-06
> **blizzard1563 said:**
> I tried a live CD and it just wanted to install Ubuntu in a second partition. It wont even give me that option with the windows CD. Some how i need to get windows on the computer. I don't have a problem keeping Ubuntu but i do not know how to make a new partition for windows

You can use the live cd(use w/out installing) to use gparted as mentioned. Then either create a separate partition for windows to use or install windows then put ubuntu on beside it afterwards.

---

### Post by maxar6 on 2011-08-06
You could use a ubuntu live cd to wipe the hardrive if you do not have enough space.

---

