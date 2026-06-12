---
title: "where can i see partition drives"
date: 2010-10-23
forum: General Help
---

### Post by forgottencid on 2010-10-23
Can anyone help me..I have question, where can I see the drives that I partition when installing ubuntu?
just like in Windows if you go in MY COMPUTER you can see LOCAL DISK C and LOCAL DISK D?
please help me
I am a newbie..
thanks AND GODBLESS!:)

---

### Post by kgarbutt on 2010-10-23
Use gparted. You can use it to view the partitions in a graphic format. Install it from the terminal like this:

sudo apt-get update
sudo apt-get install gparted

---

### Post by forgottencid on 2010-10-23
[@kgarbutt]("http://ubuntuforums.org/member.php?u=719803")
how can i do that? huhu!
sorry for inconvience...:)

---

### Post by cpmman on 2010-10-23
System - Administration - Disk Utility

---

### Post by forgottencid on 2010-10-23
there is n disk utility under system>administration?:(

---

### Post by cpmman on 2010-10-23
Try System - Preferences - Main Menu and check if it is ticked to appear.

What version of ubuntu are you running?

---

### Post by forgottencid on 2010-10-23
i am running ubuntu 9.04...
i ll attach some pic so that what i want to look like..
look at the left sied of the pic!

---

### Post by perspectoff on 2010-10-23
If using the Ubuntu ("Regular Download") LiveCD, GParted is in System -> Administration -> GParted.

Otherwise, you will have to install it, as the other reply indicated. Once it is installed you can find it in the menu in several places (e.g. System -> Utilities -> GParted).

Start it and all your partitions will appear.

Disk Utility is not the same as GParted and does not give quite the same information.

---

### Post by Swiftjay on 2010-10-23
> **perspectoff said:**
> If using the Ubuntu ("Regular Download") LiveCD, GParted is in System -> Administration -> GParted.

Otherwise, you will have to install it, as the other reply indicated. Once it is installed you can find it in the menu in several places (e.g. System -> Utilities -> GParted).

Start it and all your partitions will appear.

Disk Utility is not the same as GParted and does not give quite the same information.

If you just wanted to see disk partitions you could do fdisk -l in root and that would show you all of the partitions you have, it also shows usb hard drives too.

This also shows mounted and unounted.


If you wanna be safe you could also do sudo fdisk -l so you don't have to be in root.

---

### Post by Ubuntows Rocks on 2010-10-23
> **forgottencid said:**
> Can anyone help me..I have question, where can I see the drives that I partition when installing ubuntu?
just like in Windows if you go in MY COMPUTER you can see LOCAL DISK C and LOCAL DISK D?
please help me
I am a newbie..
thanks AND GODBLESS!:)

You could just get GParted from Ubuntu Software Center (under applications tab)

---

### Post by perspectoff on 2010-10-23
> **forgottencid said:**
> 
just like in Windows if you go in MY COMPUTER you can see LOCAL DISK C and LOCAL DISK D?


BTW, the nomenclature Local Disk C: and Local Disk D: in windows does not have a one-to-one correlation to partitions, so the comparison is not exactly accurate.

Windows gives drive letters to all kinds of things, such as network drives, virtual drives, and on and on. A drive letter in Windows may or may not correspond to a partition.

---

### Post by Ubuntows Rocks on 2010-10-23
> **perspectoff said:**
> BTW, the nomenclature Local Disk C: and Local Disk D: in windows does not have a one-to-one correlation to partitions, so the comparison is not exactly accurate.

Windows gives drive letters to all kinds of things, such as network drives, virtual drives, and on and on. A drive letter in Windows may or may not correspond to a partition.

Confused me also but he mentioned Partitions, but since there is a "My Computer" under the places tab so... Well yes you get my point! He probably is looking for something like GParted

---

### Post by srs5694 on 2010-10-23
> **Ubuntows Rocks said:**
> Confused me also but he mentioned Partitions, but since there is a "My Computer" under the places tab so... Well yes you get my point! He probably is looking for something like GParted

Based on the screen shot in post #7, I think he's looking for disk icons on the desktop. My experience is that icons for disks and partitions that are auto-mounted by GNOME show up there, but disks and partitions handled in /etc/fstab (including the linux root and swap partitions and perhaps some others) don't turn up on the desktop. Links to those locations could be added by creating a suitable symbolic link in the ~/Desktop directory, if I'm not mistaken; however, since I don't normally run GNOME, it's not convenient for me to test that and give exact instructions at the moment.

---

### Post by Morbius1 on 2010-10-23
I think the problem may be the Label of the Windows partition.

Unless you have a line in fstab explicitly mounting the Windows partition, Places will show non system disks by label if there is one or by something like "43GB file system" is there is no label. If on Windows your "C Drive" is listed as "Local Disk C" you have no label on that partition.

As a side issue, the rule for desktop icons and fstab is this: anything mounted to your /home/username directory or to /media ( which is where Nautilus automounts partitions ) will create a desktop mount icon. Anything mounted to /mnt or to the root directory itself ( / ) will not.

---

### Post by Ubuntows Rocks on 2010-10-24
> **forgottencid said:**
> i am running ubuntu 9.04...
i ll attach some pic so that what i want to look like..
look at the left sied of the pic!

Oh... He's not looking for GParted, He's just looking at what is mounted (Post 7 attachment) e.g. under places tab click "48GB Filesystem" and it will show on the Desktop but I'm still confused with his question.

---

### Post by Ubuntows Rocks on 2010-10-24
> **srs5694 said:**
> Based on the screen shot in post #7, I think he's looking for disk icons on the desktop. My experience is that icons for disks and partitions that are auto-mounted by GNOME show up there, but disks and partitions handled in /etc/fstab (including the linux root and swap partitions and perhaps some others) don't turn up on the desktop. Links to those locations could be added by creating a suitable symbolic link in the ~/Desktop directory, if I'm not mistaken; however, since I don't normally run GNOME, it's not convenient for me to test that and give exact instructions at the moment.

Correct me if I've taken what you've said in the wrong way, but can't you simply click places tab then the "Filesystems underneath" to get it to show on the Desktop.

---

### Post by trikster_x on 2010-10-24
Places>Computer

Gives you a listing of any used drives or partitions like in windows, and allows you to mount with a double click if possible.  Once mounted, you can usually at least read the contents of the disk, with most filesystems being writable as well.  They will not be named DRIVE C:\ or similar, but more likely will be something like:

"160 GB Hard Disk:87 GB File System" or similar. 

Of course the numbers will change depending on the actual space on your hard drive and partitions, but you get the idea.  Some partitions will also be labeled rather than specifying size.

---

