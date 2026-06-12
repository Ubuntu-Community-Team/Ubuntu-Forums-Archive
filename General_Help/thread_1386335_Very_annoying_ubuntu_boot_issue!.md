---
title: "Very annoying ubuntu boot issue!"
date: 2010-01-20
forum: General Help
---

### Post by Alfieg on 2010-01-20
Please help, I want to enjoy dual booting windows 7 and ubuntu but I have an issue.

*If I select windows 7 from the boot menu (Grub or Wubi, i've tried both), it starts to boot windows 7, then the screen goes black and i'm back to the bios. If I then select Windows 7 again it boots into windows ok!!

*If I then restart the computer and select Ubuntu from the boot menu it will start to boot, but then black screen and back to the bios. If I then select Ubuntu again it boots in absolutely fine!!!

There has to be a way around this!? It's not a big deal but windows 7 tries to go into recovery mode every time and it's a bit of a ball ache.

I would hugely appreciate anyones help [IMG]http://forums.overclockers.co.uk/images/smilies/smile.gif[/IMG]

Edit: I'm using a Samsung N210 Netbook

---

### Post by steveneddy on 2010-01-20
Get rid of Wubi, partition the drive and install Ubuntu for real.

That's what all the cool kids are doing.

---

### Post by phillw on 2010-01-20
+1
For whatever reason - Wubi and Win7 are just not playing together well.
Use the partitioning tool within Win7 to make about a 10GB area of 'free' space for Ubuntu and pop on a true dual boot System.

Using Win to partition is covered here --> [Resize a Partition using Vista / Win7]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/")

Regards,

Phill.

---

### Post by Alfieg on 2010-01-20
Sorry, I should have made it more clear. I actually tried the traditional partitioning method first. It's not a wubi problem.

---

### Post by phillw on 2010-01-20
Ahhh...

I think i know what is occurring ... If you have ubuntu running, you can re-boot to ubuntu okay - several times. But as soon as you boot Win7 it breaks.

Is this what is happeneing ?

Phill.

---

### Post by Alfieg on 2010-01-20
Yes indeed. That is what's occurring and it happens if i boot windows 7 several times also (ie that will break ubuntu). 

It's not fully broken, it just forces a hard reset and works after that. Any ideas?

Thanks.

---

### Post by Alfieg on 2010-01-21
Anyone?

---

### Post by Alfieg on 2010-01-22
Sorry to bump again, but it's in the hope that someone will catch my thread and have a solution.

---

### Post by Saiko Berry on 2010-01-22
Get rid of Windows 7 and install Ubuntu. Get rid of Wubi and partition your hard drive.

---

### Post by Alfieg on 2010-01-22
As said (Twice), I have tried a proper install on a partition and I only installed wubi after to see if it still happened.

+ It's not fair to expect a new Ubuntu user to ditch windows alltogether. I have tried on a different machine and the issue does not occcur, so what sort of hardware config might cause a reboot of the computer as ubuntu loads the first time but not the second?

I will take a video later so you can see what i'm on about.

---

### Post by lordskid on 2010-01-22
Is the ubuntu partition an extended partition or a logical partition? And what bootloader are you using?

---

### Post by Alfieg on 2010-01-22
Not sure exactly, I selected the "Install side by side" option and adjusted the ubuntu install partition using the coloured slider. Gave ubuntu 9.10 30GB.

As far as boot loader i'm using whatever the default loader ubuntu installs is. (GRUB)

Basically, if I select ubuntu it starts to show the boot logo and then the machine hard resets to bios. If I then select Ubuntu again it boots normally. Same for Windows.

Thanks.

EDIT: Is it better to make a partition in Windows and install to that rather than use the linux partitioner at ubuntu install? Also, what size of partition would ou suggest?

---

### Post by SurfinBirdman on 2010-01-29
DUDE!!!

I totally understand.  I've been playing around with the same issue myself.  
definately a total ball-buster.  at first i thought i installed incorrectly, or 
partitioned it weird but to no avail.  

I even tried a few different boot loaders but nothing happened.  

and while i am a linux noob, im not a computer noob, i know what im doing here...


sadly i dont have an answer, but am interested as to what computer you are using and what kinda hardware specs.

personally ive got a dell studio xps 1340, 
i tried  a full 50gb partition for ubuntu and then thought it might be a grub issue, so i dicked wit that till i tinkered with easybcd, and nothing changed.

and most recently i went with a wubi install of ubuntu


I also would love some help with this issue instead of comments about ditching windows
and going all out linux or advce to do things ive already tried

---

### Post by Alfieg on 2010-02-07
> **SurfinBirdman said:**
> DUDE!!!

I totally understand.  I've been playing around with the same issue myself.  
definately a total ball-buster.  at first i thought i installed incorrectly, or 
partitioned it weird but to no avail.  

I even tried a few different boot loaders but nothing happened.  

and while i am a linux noob, im not a computer noob, i know what im doing here...


sadly i dont have an answer, but am interested as to what computer you are using and what kinda hardware specs.

personally ive got a dell studio xps 1340, 
i tried  a full 50gb partition for ubuntu and then thought it might be a grub issue, so i dicked wit that till i tinkered with easybcd, and nothing changed.

and most recently i went with a wubi install of ubuntu


I also would love some help with this issue instead of comments about ditching windows
and going all out linux or advce to do things ive already tried

found a solution yet mate?

---

### Post by oldfred on 2010-02-07
To see if there are any booting issues you can run this script.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.


If you are able to boot ok after a hard reboot the script may not show anything. There have been issues with HP & Dells that totally corrupt the boot loader in the MBR but I have not seen were reboot works once corrupted. Does the Dell media software do something special?

HP ProtectTools and Dell Recovery Tool write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)

---

### Post by Alfieg on 2010-02-07
perhaps it is something to do with the system recovery partition?

---

### Post by Alfieg on 2010-02-08
Ok, so i've tried 10.04 Alpha 2 and the problem is gone. I then went back to 9.10 and the problem is back. can anyone explain this?

---

### Post by Alfieg on 2010-02-09
So is this something to do with Grub2? I really would appreciate some help on this one. Does 10.04 use a different grub?

---

### Post by Alfieg on 2010-02-09
Ok, I think I may have sussed it. I think the grub loader has been put on my system recovery partition and that's what is causing the problem. Is there a way of:

A) finding out where grub is located and
B) moving it?

Thanks

---

### Post by oldfred on 2010-02-09
The boot_info_script shows where everything is including boot loaders in MBR and PBR and how it relates. I do not know how to uninstall grub but there are lots of instructions on installing grub, grub2 or windows boot loaders.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

