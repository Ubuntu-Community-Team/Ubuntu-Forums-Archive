---
title: "Ubuntu to IDE USB Drive via Win 7"
date: 2012-09-28
forum: General Help
---

### Post by Earl-Grey on 2012-09-28
Hello there,

I am trying to install a copy of Ubuntu on my IDE drive which is connected to my WIN7 pc at the moment.

I have tried using Wubu but it doesnt load. 

Is there a good way to do this?

---

### Post by oldfred on 2012-09-28
Is the IDE drive a bootable drive?

If so just install Ubuntu to that drive and be sure to install the grub2 boot loader to the MBR of the external drive.

Install to external drive 11.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by Earl-Grey on 2012-09-28
Ahh, I think that I am missing the Grub Loader.

Can I install this through Windows and should it be done after wubi is installed?

---

### Post by Earl-Grey on 2012-09-28
> **Earl-Grey said:**
> Ahh, I think that I am missing the Grub Loader.

Can I install this through Windows and should it be done after wubi is installed?

I installed Grub but now i just have a black and white grub dos screen when I switch on my pc with no windows.

Do you know a grub command to load ubuntu?

---

### Post by oldfred on 2012-09-28
If you install wubi, you use the Windows boot loader. There is a grub menu after the Windows boot loader, but it is only loading Ubuntu and not booting system.

From an Ubuntu liveCD install this or download the full RepairCD.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

If you have Windows repairCD, you can also use that to reinstall the Windows boot loader.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

But if you are willing to use a separate drive, then you should think about a full install.
From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

---

### Post by Earl-Grey on 2012-09-29
If you install wubi, you use the Windows boot loader. There is a grub  menu after the Windows boot loader, but it is only loading Ubuntu and  not booting system.

>>Not sure if I fully understand, but it isn't loading Ubuntu, it loads a black and white grub screen and is waiting for me to type some grub commands in.

From an Ubuntu liveCD install this or download the full RepairCD.

>>I am sorry I dont have access to a CD drive and cannot boot by my usb cd drive with my bios. That is why I am trying to install Wubi with Win7.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report  (Other Options) & post the link it creates, so we can see your exact  configuration and diagnose advanced problems.

If you have Windows repairCD, you can also use that to reinstall the Windows boot loader.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

But if you are willing to use a separate drive, then you should think about a full install.
From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/0...o-wubi-ubuntu/]("http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/")
Agostino: Wubi actually wasn’t designed to do long-term installations.  The main aim was really to let people try out Ubuntu with confidence.  Normally, users that start with Wubi tend to upgrade to a full  installation to a dedicated partition at the next release cycle.

---

### Post by Earl-Grey on 2012-09-29
At the moment I have partitioned my main C drive so now I have a small C drive for Win7 and 80 Gb for Ubuntu.

I have installed Ubuntu via the Wubi on this 80 gb drive.

The only problem I have is loading Ubuntu.

I have also used EasyBCD to try and put Ubuntu in the Boot menu, but cannot get it to work.

Do you have any help in getting Ubuntu to load?

---

### Post by oldfred on 2012-09-29
I do not know EasyBCD and prefer grub especially if you can boot from a second drive.

[http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
dual boot Windows 7 & Ubuntu 12.04 with EasyBCD
[http://ubuntuforums.org/showthread.php?t=2038652](http://ubuntuforums.org/showthread.php?t=2038652)

---

