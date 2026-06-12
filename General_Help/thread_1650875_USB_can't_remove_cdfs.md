---
title: "USB can't remove cdfs?"
date: 2010-12-22
forum: General Help
---

### Post by LuniTux on 2010-12-22
Hello,

I have a 1GB USB drive that has a cdfs partition. the cdfs partition was created when I was trying to install ubuntu on the drive via [http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar]("http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar"). The drive does not have any U3 capabilities so the U3 uninstaller does not work. Is there any way to remove the cdfs drive?

Thanks,

---

### Post by MooPi on 2010-12-22
Have you tried gparted ? It is an excellent partitioning tool that is in the Ubuntu repository.

---

### Post by LuniTux on 2010-12-22
I just tried it. It will not show the cdfs part of the USB but it successfully formats the USB. The fake cdrom still exists. I also checked the properties of the fake cdrom and it says that it is an **isofs** not a **cdfs**

---

### Post by MooPi on 2010-12-22
Can you give me a screenshot of gparted in action with the usb drive highlighted.

---

### Post by LuniTux on 2010-12-22
Here is the file. (zipped is for if the original is resized by the website)

---

### Post by MooPi on 2010-12-22
From the screenshot it looks as if your good to go as the drive is completely vfat formated. One p[ossible glitch is as you said it's hidden. In that case try to delete the entire partition then create a new partition table and new partition after that.

---

### Post by psusi on 2010-12-22
There is no such thing as "cdfs".  That is just what dumb-dumb windows calls iso9660.  And yes, the gparted screen shot clearly shows it is correctly formatted as fat.  What exactly is still wrong?  You boot into windows and it thinks it is a cd?

---

### Post by LuniTux on 2010-12-22
I tried that and the isofs still remains. I also tried ```
sudo dd if=/dev/zero of=/dev/sdb

```
from the website [http://www.linuxquestions.org/questions/linux-general-1/remove-linux-partition-on-usb-flash-drive-693787/]("http://www.linuxquestions.org/questions/linux-general-1/remove-linux-partition-on-usb-flash-drive-693787/")

and that did not work either. I tried using the method at the end of that forum but still no good. The USB is only 1GB so if there is no solution found I can just toss it but I would still like to know how to fix it. I noticed that the fakecdrom (isofs) has autoplay files in it.

autorun.exe
autorun.dat
autorun.inf

don't know if that helps any.

Thanks for all the help

---

I know that fdisk created the isofs so would that mean that fdisk can remove it?

---

### Post by LuniTux on 2010-12-22
When I use the usb drive in windows, the autorun starts as if it were a real CD. it also shows an extra cdrom drive in my computer with the autorun files in it.

---

### Post by psusi on 2010-12-22
Can you be more specific about what you mean when you say that there is a cd?  Where are you seeing this?  What exactly do you see?

That dd command absolutely, positively wiped out everything on the disk.

---

### Post by psusi on 2010-12-22
> **LuniTux said:**
> When I use the usb drive in windows, the autorun starts as if it were a real CD. it also shows an extra cdrom drive in my computer with the autorun files in it.

Do you see TWO drives show up in windows when you plug in the drive?  The only thing I can think of is that the stick is pretending to be BOTH a disk drive, and a cdrom, in order to trick windows into running software on it.

---

### Post by LuniTux on 2010-12-22
Sorry if I was not detailed enough. here are the windows snapshots. One of my computer and one of the fake cdrom.

---

### Post by psusi on 2010-12-22
Yep, both show up, so it's a messed up hardware thing that stick is doing to trick windows into running software.

---

### Post by LuniTux on 2010-12-22
Is it something that can be fixed or should I just call it a loss and buy a new one? It's only 1GB

---

### Post by psusi on 2010-12-22
How about you just ignore the silly fake cd drive?  Or installing the software on it should take care of it.

---

### Post by LuniTux on 2010-12-22
I can ignore it in ubuntu but in windows the autorun starts and opens some "bankofamerica" website. Not sure why that is what opens but it does

---

### Post by MooPi on 2010-12-22
That sounds as if it's not related to the Ubuntu install on the drive. But is an autorun virus that was most likely on the drive before the partitioning.

---

### Post by LuniTux on 2010-12-23
That would make sense now that I think about it. I checked with my girlfriend (the person who gave me the drive) and she said that she got it from some bank thing at her college... Im not sure why It did not show up until after I tried the Ubuntu install though. oh well.

Thanks for all the help!

---

### Post by ash_ketchume on 2010-12-27
I don't mean to revive this thread or anything, but I have the same problem. 
Only, it's on a 1tb hard drive. It's a write protected cdfs partition (mean to contain some encryption software for the hdd), and it seems nothing can delete it. I've tried Gparted, Diskpart, and various other partitioning programs, and was wondering if anyone else can think of anything.

---

### Post by carra on 2011-06-07
This problem is not solved!
Please *mods*, update the thread's name!

---

### Post by CharlesA on 2011-06-07
> **carra said:**
> This problem is not solved!
Please *mods*, update the thread's name!
If you have a similar problem, create a new thread for it, as this one is old and it does look like it is indeed solved.

Thanks.

---

