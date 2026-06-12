---
title: "Which file system for external HDD?"
date: 2010-08-29
forum: General Help
---

### Post by phase constant on 2010-08-29
Hello I just picked up a 1 TB Western Digital.

Right now i just have Ubuntu 10.04 installed but I think I will need to dual boot with winblows soon for school. :-(

Which file system will play nice with both OS's? 

Should I try to put one of the OS's on the external HDD or install them both on the internal (250 GB Seagate)?

:popcorn:

---

### Post by sparkchen on 2010-08-29
My current solution for your reference:
Install Windows on NoteBook inside HDD;
Install Ubuntu on external HDD(40GB) as single partition.
Maybe it does not work for you.
After all your external HDD is too large(1TB),single partion is a waste and you can not use the partition in Windows.
Sugest you format your external HDD into at least two partition,one for ubuntu and the other one for Windows.

---

### Post by jcolyn on 2010-08-29
I have a couple of external drives which are used for backup. Both are formatted NTFS. From my Windozz days. My Linux OS can read and can copy files to them.

If you are going to dual boot the [COLOR=Blue]**easiest**[/COLOR] way is to first backup any files you need to keep then wipe the entire drive. Next is to install Windozz. Once you have it fully updated and the programs you plan to install right-click my computer and choose manage (something like that) then shrink the partition.

Next insert the Linux install disk. When you get to the partition part choose the run side by side button then finish the install.

If all goes well at reboot you'll have a grub selection to dual boot either Windozz or Linux.

---

### Post by phase constant on 2010-08-29
> **sparkchen said:**
> My current solution for your reference:
Install Windows on NoteBook inside HDD;
Install Ubuntu on external HDD(40GB) as single partition.
Maybe it does not work for you.
After all your external HDD is too large(1TB),single partion is a waste and you can not use the partition in Windows.
Sugest you format your external HDD into at least two partition,one for ubuntu and the other one for Windows.

Ok but won't Ubuntu run slower off the external HDD?

I really just want to know which file system (FAT, NTFS, ext3, ext4) to use.

I think I will transfer what I need right now, scrub my internal HDD. And then set up dual boot. Would that be my best route?

---

### Post by sparkchen on 2010-08-29
> **phase constant said:**
> Ok but won't Ubuntu run slower off the external HDD?

I really just want to know which file system (FAT, NTFS, ext3, ext4) to use.

I think I will transfer what I need right now, scrub my internal HDD. And then set up dual boot. Would that be my best route?

My Ubuntu run very smoothly on external HDD.
I format my external HDD as ext4 filesystem.
I Install Ubuntu on exxernal HDD because i can boot my system not only my computer,but also other's computer.
Then no need carry a notebook instead of a external HDD with Ubuntu and my docuement inside when travel or businnes trips.

---

### Post by uRock on 2010-08-29
If you want to be able to see it via a Windows machine, then use NTFS. Otherwise, use EXT4.

---

### Post by phase constant on 2010-08-29
> **uRock said:**
> If you want to be able to see it via a Windows machine, then use NTFS. Otherwise, use EXT4.

Ok I just want to double check I can view it from Ubuntu.

In the Disk Utility it says:

"NTFS: The native Windows file system. Not widely compatible with other operating systems than Windows"

---

### Post by uRock on 2010-08-30
I have had no problems accessing, moving, making nor deleting files from the NTFS partitions, while using Ubuntu.

---

