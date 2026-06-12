---
title: "OS select?"
date: 2010-12-02
forum: General Help
---

### Post by Fastlane350 on 2010-12-02
Hello Ubuntu community,
   I am a new Ubuntu user (10.10 maverick  meerkat). I installed the system about 3 days ago and I have been  playing around and enjoying my new OS ever since. I am still sort of new  to everything so there are lots of things i am still trying to learn(I  managed to get Compiz working pretty well though :grin:).  What has honestly been the most difficult for me was getting any  program through the WINE app to work. Im not quite ready to try to  figure out how to sync my ipod without itunes yet, and honestly i just  think microsoft office is much better than open office. 
    I am  currently a University student and for now id still like to be able to  use a few of my windows programs, however until i get a chance to read a  book or 2 about ubuntu and get a little bit more familiar with entering  commands through the terminal I would like to be able to boot my  computer up in the windows OS also. 
    I was wondering if someone  could help me setup a OS selection option for my computer start-up. I  installed windows 7 right before I got Ubuntu 10.10 running, and I am  pretty sure I opted to run Ubuntu alongside windows so it should still  be there. When I start-up though my computer immediately loads Ubuntu.  Help?

---

### Post by gdonwallace on 2010-12-02
I guess the first question would be when You installed Ubuntu did you choose the option to use the entire partition? (meaning the entire hard drive) If so, then windows is gone. If it is booting into Ubuntu, then either grub is messed up or you over wrote your Windows install.

I would suggest downloading and burning a copy of rescuecd.  Google the name and it will take you to their website.  There is a manual online with instructions on how to fix the boot manager (grub).  If Ubuntu is installed along side Windows this will fix the problem and allow you to choose what OS You want to boot into.

Depending on your machine, if Ubuntu is the only OS installed You might want to look at VirtualBox.  VirtualBox will allow you to install Windows inside a virtual hard drive from within Linux.  It uses Your computers resources (i.e. CPU, memory, net card, video, etc) so it can be pretty taxing on an older machine, but it must have Windows for certain programs it is a good alternative.  Virtualbox is available through the Software Center, install from there.  There are lots of tutorials and how too's available on how to install another OS in VirtualBox.

You should also check the Wine Website, they have information on how to install different programs from windows and information on how to get work arounds for programs that don't work "out of the box".  The information is helpful and pretty easy to follow.

---

### Post by efflandt on 2010-12-02
Post what you get in a terminal for the output of: **sudo fdisk -l** (small L)

Highlight what you paste from that and wrap it with code tags by clicking the **#** at top of message window to keep its formatting.

Or for more info you could run the boot info script [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Fastlane350 on 2010-12-02
```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cc214

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       37333   299869184   83  Linux
/dev/sda2           37333       38914    12699649    5  Extended
/dev/sda5           37333       38914    12699648   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20b120b0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      155058    78149200+   7  HPFS/NTFS
```

---

### Post by Fastlane350 on 2010-12-02
Lets assume that i deleted windows, because it is entirly possible when i installed Ubuntu i deleted it. I was not familiar with the term partition at the time so i sorotf clicked whatever made the most sense to me. I cannot recall what that was but i thought it was going to keep windows.  
  Anyway ill give you a quick breakdown. This is an older machine, the processor sucks. It previous ran off of 2 90gb hard drives till the primary one failed. Now it runs off 1 320gb PATA hard drive and the old 90gb IDE drive. 
   The virtual box sounds like a great solution but will it be much slower than if i were to just run it alongside ubuntu? i dont want to wait for 3 days while my computer download office 2010 from the university servers because my cpu is running at 99% capacity. It would be like waiting for UPS to deliver a package in a 1982 Geo Tracker from canada going uphill through a foot of mud.   At the same time i really only want windows for Office and Itunes until i can sit down for a few days and just figure out how to get it onto this OS. (trust me i tried for hours, office wanted some MSXML file that i spent an hour finding only to discover a new error at the next step of office installation...this is why i decided to quit using microsoft yet it still taunts me)

---

### Post by gdonwallace on 2010-12-02
As VirtualBox uses the resources on your system to power Windows, it could slow the system down pretty good.  For instance, if you have 2 gig of memory, you would have to decide how much of that memory to split between Ubuntu and the Virtual Windows that You are running.  This also goes the same with your processor, video ram, and network card.  The upside is that Virtualbox will create a virtual hard drive, that while You are not running windows, that it does not use those resources.

As for downloading, You can download Office into Ubuntu, burn it to CD, launch windows and then install it that way.

---

