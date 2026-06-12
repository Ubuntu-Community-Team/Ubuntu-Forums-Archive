---
title: "Is dual booting like this possible?"
date: 2011-09-17
forum: General Help
---

### Post by nslegacy163 on 2011-09-17
I just re-formatted and partitioned my internal drive for the reason explained in this previous post of mine which you may want to [read]("http://ubuntuforums.org/showthread.php?t=1845211"). 

 Attached is a hand-made (tada!) shot of what the gparted looks like for my drive now and how I'd like it to work if it can. 

 I have a usb iso of 10.10 that I was using before I needed to reinstall Windows and I have Win7 on a DVD. I thought that if I have two partitions on the same physical disk I could just load 10.10 to one and Win7 to the other since Windows typically just nukes any other OS you have, right? 
 So I'm assuming I need both partitions (sda1 Ubuntu and sda3 Win7)  to have boot flags...? But I can't...? I click boot flag on one, the other goes away. So how can/does this work? Thanks!

---

### Post by nslegacy163 on 2011-09-17
Quick add-on: 

 I obviously don't mind having to load Win7 first then 10.10 since the drive is already clean. So if that's the way to do it, please let me know also! 
 Thanks again in advance.

---

### Post by ottosykora on 2011-09-17
as you found out yourselve, it is not possible, that is why people had to develop things like boot managers.

Now it i sonlyl a question if you want use the boot manager from windows or linux.

For w7 you should have two partitions, for linux one for /root and one for /home. Then all will work either with windows boot manager or grub, this would be the boot manager of ubuntu.

---

### Post by TeoBigusGeekus on 2011-09-17
> **nslegacy163 said:**
> Quick add-on: 

 I obviously don't mind having to load Win7 first then 10.10 since the drive is already clean. So if that's the way to do it, please let me know also! 
 Thanks again in advance.
Spot on. That's exactly the way to do it.

---

### Post by nslegacy163 on 2011-09-17
Alright so I can keep the partitioning the way I have it and load Win7 to one and then use the live USB to load 10.10 to the other? Win7 won't om nom nom my partitions?

---

### Post by TeoBigusGeekus on 2011-09-17
No. And even if it does, you can fix everything afterwards.

---

### Post by thebarisaxkid on 2011-09-17
Install Windows 7 first, then Ubuntu. If you install the other way around, Windows 7 boot loader will overwrite GRUB. It will not recognize Ubuntu (or any *nix distros) either. (So you would only boot straight to windows with no options). Doing it the other way around, GRUB overwrites Win7's bootloader, and it can still recognize both OS's.

Windows first, then your *nix distros.

---

### Post by thebarisaxkid on 2011-09-17
Forgot about partitoning. If your installer CD for Windows 7 has a partition manager, make sure you install to the partition you want to. If it will only use the whole space on the disk, then after your install is done, you will have to shrink the Windows 7 partition, either using the one  built into windows (right click Computer > Manage) or Gparted from the liveCD. Then install Ubuntu to the other partition

---

### Post by Blasphemist on 2011-09-17
Here's what I'd want to end up with. Windows installed first and using ntfs file system. That will be one primary partition. I'd then shrink that to whatever size I want using GParted on the live iso. Then create an extended partition in all of the available space. That is a second and last primary partition. Within the extended partitiion, create logical partitions for any desired distros or mount points for distros. Create a logical swap partition at the end of the disk that is a bit bigger than the amount of memory. Allow for adding memory if desired. When installing ubuntu use the manual disk allocation option to direct ubuntu to use specific partition or partitions.

---

### Post by Alan F on 2011-09-17
Install Win7 to the disk. You will find it creates 2 partions. One of 100MB (Part 1) the other the rest of the disk (Part 2 C\:).

Fire up Win7 and using Disk Management shrink the C\: to desired size.

In the remaining free space create 2 partitions, Part 3 for Ubuntu and Part 4 for Share. Format Part 4 NTFS. Win7 will allocate this a drive letter, probably E\:

Install Ubuntu to Part 3 using the Advanced option dividing up the space betweeen \ and swap as required.

---

### Post by Blasphemist on 2011-09-17
> =Alan F;11260110]Install Win7 to the disk. You will find it creates 2 partions. One of 100MB (Part 1) the other the rest of the disk (Part 2 C\:).

Fire up Win7 and using Disk Management shrink the C\: to desired size.
I've never had good luck with windows being able to do a real good job shrinking its own partition while it is in use.

> In the remaining free space create 2 partitions, Part 3 for Ubuntu and Part 4 for Share. Format Part 4 NTFS. Win7 will allocate this a drive letter, probably E\:

Correction, create the extended partition that I described. Then within it creating these as logical partitions would be fine, along with a swap partition.

> Install Ubuntu to Part 3 using the Advanced option dividing up the space betweeen \ and swap as required.
/ (root mount point) and swap are on separate partitions and since you create the swap above you will not need to anything about swap during the install.

---

### Post by nslegacy163 on 2011-09-17
Thanks everyone. You all had valid and helpful tips to get this done successfully! I have Win7 and 10.10 running swimmingly on the machine! Someday I think I'll just have two separate machines and a KVM...haha Switching between OS's is a pain. #firstworldproblems Hahaha

Take care.

---

### Post by Rasa1111 on 2011-09-18
haha! Niice handmade shot! :)
did you know that you can just hit Alt+Prtscr, and it will take a shot of the open window for you.?

---

### Post by nslegacy163 on 2011-09-18
> **Rasa1111 said:**
> haha! Niice handmade shot! :)
did you know that you can just hit Alt+Prtscr, and it will take a shot of the open window for you.?

Yes, but the screen shot was on the desktop being formatted and partitioned with no interweb connection. I posted this thread from my netbook, running ubuntu 11.xx of course! 

 Plus I like to draw. Haha

---

### Post by Rasa1111 on 2011-09-18
haha, cool!
well you did good on it! :P

---

### Post by Alan F on 2011-09-18
[QUOTE=Blasphemist;11260160]I've never had good luck with windows being able to do a real good job shrinking its own partition while it is in use.

With Windows 7 my experience is exactly the opposite. Windows partitions can be created and resized correctly from Disk Management with windows running.

If Windows partitions are resized using Gparted then Windows insists on carrying out a scan of resized partition when restarted suspecting that errors have occured.

---

### Post by Blasphemist on 2011-09-18
> **Alan F said:**
> [QUOTE=Blasphemist;11260160]I've never had good luck with windows being able to do a real good job shrinking its own partition while it is in use.

With Windows 7 my experience is exactly the opposite. Windows partitions can be created and resized correctly from Disk Management with windows running.

If Windows partitions are resized using Gparted then Windows insists on carrying out a scan of resized partition when restarted suspecting that errors have occured.

The detail of my poor experience with windows doing the shrinking is that it refuses to give me enough of the available space. The shrink runs a defrag then tries to shrink. When it comes back telling me it can only give me a small portion of the available space it refers me to appication error log to see what limited it. There is always something new that is the limiting factor. I figure a way around that in turning off a service temporarily or something and go through the process again and a new limit smacks me.

Yes, when GParted does the shrinking windows wants to do a chkdsk, it does successfully on the first windows boot and everything is then hunky dorry.

---

