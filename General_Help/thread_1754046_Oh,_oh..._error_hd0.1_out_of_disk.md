---
title: "Oh, oh... error: hd0.1 out of disk?"
date: 2011-05-09
forum: General Help
---

### Post by Common_Sense on 2011-05-09
So I'm running ubuntu 10.04 64 bit on my pc and I can't boot! During startup I see this:
> 
error: hd0.1 out of disk
grub rescue>
When I try to reinstall it tells me that the disk encountered a boot install error and that I will be redirected to the live desktop in which I should investigate the matter further. I can't find anything so I just install as normally and during reboot I see this again:
> 
error:hd0.1 out of disk
grub rescue>
I have reinstalled several times and this is all I get. A friend told me that my bios may be corrupt.

So, uh, Help!!! What do I do???

---

### Post by 3 frags left on 2011-05-09
This thread may be helpful:
[http://ubuntuforums.org/showthread.php?t=1331730](http://ubuntuforums.org/showthread.php?t=1331730)

Also, next time you install Ubuntu, leave the /boot folder in a separate partition (100MB is enough), it helps a lot by making recovery more practical.

---

### Post by Common_Sense on 2011-05-09
I'll try that right now. Thanks!

---

### Post by Cybie257 on 2011-07-17
I'm getting this error with an interesting method of installing Ubuntu, which has never failed me in the past. 

Using Windows 7 x64, I also have VMWare Workstation 7.1. With VMWare, in order to speed up the Ubuntu Install process, I attach a physical drive to the VM, attaching the Ubuntu ISO as a CD, then starting the VM and installing. 

After all is installed, I am (usually) able to reboot the VM without problems and do whatever I do. Also, because Linux is so superior in this fashion compared to Windows, I am able to boot the physical machine from that physical disk as if I had installed the system as normal and not through VMWare. (Of course, if I want proprietary hardware drivers for the physical machine (IE:nVidia), I just install them and go). After installing such drivers, I am (usually) still able to boot into it as a Virtual Machine and everything works as good as can be.

Now, after installing and mounting the drive with EXT2FDS in Windows, I get the Out Of Disk error when trying to boot into VMWare. NOTE: First inistial boot (2-3 times tested), I was able to boot into Linux just fine. Even though I get the error when attempting to boot through VMWare in Windows Host, I am able to fully boot into Ubuntu with the physical machine (Same Exact Physical Hard Disk). No errors. I'm thinking this is a problem with VMWare since 7.x.x came out as I have never seen this problem before. 

Has anybody used this method? Getting the Errors?

System: Physical Windows 7 x64 with VMWare Ubuntu VM(Get Errors)
        Physical Ubuntu (No Errors), SAME Physical Disk Drive
        Ubuntu Version: 11.04

-Cybie

---

