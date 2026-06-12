---
title: "problem 64 bit install on Gigabyte board with SATA controller"
date: 2010-09-08
forum: General Help
---

### Post by dag1 on 2010-09-08
I am able to install the 32 bit version of ubuntu.
But since I have an AMD Phenom II x6 1055T I wish to use 64 bit version
The Gigabyte site has no drivers for ubuntu
The gigabyte manual specifies that during the OS installation (Windows) I should 
use their CD to install the SATA controller.
It has no driver for Linux

So the installation gets stuck. I tried many times. The furthest that I get is just after entring time zone and the name of the computer and choosing partition. Then it starts to format the partitions but gets stuck.

Any advise ?


Dag

---

### Post by 3Miro on 2010-09-08
If 32-bit Ubuntu works fine without extra drivers, then 64-bit should work fine as well. Are you using a 10.04 or 10.04.1 CD. You can try to format the drivers first (select "try Ubuntu" then go to GParted) so that during the install you will only select which partitions you want to use without the need to format them.

---

### Post by dag1 on 2010-09-08
I am using the 10.04.1 CD (both the 32 bit and the 64 bit CDs).
I tried both Ubuntu and Kubuntu, no difference.

One interesting point: the only way I can even get the 64 bit install CD to start is if I set in my BIOS
the SATA controller to be in the IDE mode (rather than AHCI mode.

I tried what you suggested.
First I installed 32 bit version and did all the partitioning.
Then I chose from the 64 bit CD the option to just use Ubuntu (not instlal)
Then from inside Ubuntu (64 bit) I clicked on the Install Ubuntu 10.04.1 LTS
I got up to the point where I need to decide about partitions. I chose to leave the partitions as is.
But the I get the error:

   "Installer encountered an error copying files to the hard disk:

Errno 5: Input/output error


Please advise.

thanks
Dag

---

### Post by 3Miro on 2010-09-08
If 32-bit works fine and input/output error occurs for 64-bit only, then the problem is not the driver, but the CD itself. You probably got a defective burn on the CD. Here is how you can check the CD for errors under both Ubuntu and Windows:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Or you can just redownload the .iso file and burn another Ubuntu CD. When you are burning a CD with and OS on it, then it is best to use slower speed (i.e. 8x).

---

### Post by dag1 on 2010-09-08
I downloaded the 64 bit iso again
I checked the md5sum. It is ok
I try installing. 
Still, after I enter the time zone and name, and choose to erase and  install over  the existing partition the installation just stops and hangs.

I dont think the problem is with the checksum

Dag

---

### Post by dag1 on 2010-09-08
I get the same Error 5 Input/Output error


By the way. Now I see that even when I choose to just use the Ubuntu 64 bit and not install it
I cannot open folders nor drives. It seems like the I/O is not available .

Advise ?

---

### Post by ronparent on 2010-09-08
I don't remember the specifics, but someone on another post this morning described the same problem. Their solution was to plug into ports not on the Gigabyte SATA chipset. You might check that out.

---

### Post by dag1 on 2010-09-08
Even if I choose in the bios to set the SATA controller for regular IDE still
ubuntu 64 cannot proceed in installation

Windows XP and Ubuntu 32 bit have no problem.

Dag

---

### Post by dag1 on 2010-09-08
I came across this link:
[http://www.h-online.com/open/news/item/Performance-problem-in-AMD-s-Phenom-II-X6-under-Linux-993127.html](http://www.h-online.com/open/news/item/Performance-problem-in-AMD-s-Phenom-II-X6-under-Linux-993127.html)

It seems like the Linux kernel may have problems with the AMD CoolNQuite mode.

Do the UBUNTU developers know about this ?

Is there a fix for this problem ?(from the above link it appears that the FEDORA distribution have a fix)

I disabled this CoolNQuiet mode in the BIOS.
But as before, after about 22% into the "Copying files" of the installation I get the Error 5 input/output error and the installer stops

---

### Post by dcstar on 2010-09-09
> **dag1 said:**
> 
........
But as before, after about 22% into the "Copying files" of the installation I get the Error 5 input/output error and the installer stops

Download the beta 10.10 release CD and see if the newer kernel works.

---

### Post by cascade9 on 2010-09-09
I've had no issues with the gigabyte here with linux, but I'm not using a X6 CPU. 

What model motehrboard, and are you using some SATA expanaison ports, or the nVidia/ATI SATA controller? 

> **dag1 said:**
> I came across this link:
[http://www.h-online.com/open/news/item/Performance-problem-in-AMD-s-Phenom-II-X6-under-Linux-993127.html](http://www.h-online.com/open/news/item/Performance-problem-in-AMD-s-Phenom-II-X6-under-Linux-993127.html)

It seems like the Linux kernel may have problems with the AMD CoolNQuite mode.

Do the UBUNTU developers know about this ?

Is there a fix for this problem ?(from the above link it appears that the FEDORA distribution have a fix)

I disabled this CoolNQuiet mode in the BIOS.
But as before, after about 22% into the "Copying files" of the installation I get the Error 5 input/output error and the installer stops

From the link, thats not a generic coolNQuient problem, is just from turboboost on the new X6 "T" CPUs. 

Intel turboboost took a  little while to get going, and I'm not sure if its 100% yet.

---

