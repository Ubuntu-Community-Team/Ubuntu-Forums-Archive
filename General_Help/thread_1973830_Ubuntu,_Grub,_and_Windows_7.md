---
title: "Ubuntu, Grub, and Windows 7"
date: 2012-05-05
forum: General Help
---

### Post by sjjubb1989 on 2012-05-05
Hello,
So recently I have set up my new computer (craigslist finds many deals for those of you in the US ). Anyway, I have three hard drives hooked up in this order, My first hard drive has Windows 7 on it (C:, or /dev/sda1), My second hard drive which holds my Ubuntu installation (/dev/sdb1), and then my third drive which is just a backup.

My first drive I have my Windows boot loader on it, with two entries: One for Windows 7 and one for Ubuntu. My second hard drive I installed Grub onto, which has a menu for the various kernels and of course to boot up Windows. 

Here is my issue and what I did to try to solve it, but to no avail. Every time I boot into Windows, everything is fine until I restart my computer or shut down. After I exit Windows, and try to boot into Ubuntu, Grub can no longer see my Ubuntu installation (No such device found, no partition found). Of course my second hard drive is fine, I am able to boot into my recovery CD and fix Grub after a few hours, and boot back into my Ubuntu. But the second I launch Windows 7, it screws with my Ubuntu boot partition somehow. Grub is fine, it has the right menu but is Unable to see any hard drive except /dev/sda1 [Windows].

So I want to install Grub to my Windows boot loader, /dev/sda, but to have my boot partition on /dev/sdb3 (I just re-sized my partition for 500 megabytes specifically for /boot). I tried following a tutorial on the internet to install Grub, however I am afraid if I choose to install my Grub onto /dev/sda, that it will somehow corrupt my Windows Partition.

How do I install just the boot loader onto /dev/sda while having the Grub Stage 2 files on my /dev/sdb3 partition? Also, how to I configure Ubuntu to mount /dev/sdb3 as /boot automatically, as that partition was not originally there when I installed it.

---

### Post by kidhudi on 2012-05-05
use a progam called easybcd you can set up the windows bootloader easily.

---

### Post by sjjubb1989 on 2012-05-05
> **kidhudi said:**
> use a progam called easybcd you can set up the windows bootloader easily.

I used that program to set up the Windows boot loader, however grub on my second drive containing my Ubuntu installation get corrupted whenever I boot into Windows. Is it possible to install Grub to the MBR of Windows while having the Grub files on my second drive?

---

### Post by kidhudi on 2012-05-05
in easybcd use grub2 in the dropdown menu for ubuntu. it should find it no problem then set windows 7 drive as the master boot record holder.

---

### Post by sjjubb1989 on 2012-05-05
> **kidhudi said:**
> in easybcd use grub2 in the dropdown menu for ubuntu. it should find it no problem then set windows 7 drive as the master boot record holder.

EasyBCD Finds it, however my problem is not with the Windows bootloader not loading into the Linux Grub, it is in fact a problem with Grub corrupting itself, or more so Windows corrupting Grub on my second hard drive whenever I boot Windows. If I fix Grub then I can boot into it using the Windows boot loader. But it is whenever I select Windows and then shut the computer down, that when I next boot into Grub grub is unable to find the drive that it is in fact running off of.

---

### Post by oldfred on 2012-05-05
I do not know easyBCD but do know grub.

If you have Windows in one drive and Ubuntu & grub in the other drive they should not interfere with each other.

Post link to report that Boot-Info creates from this, so we can see what is where:

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

Some with one drive and Windows software with DRM - digital rights managers has issues as grub & the drm write into the same sectors after the MBR.Then EasyBCD may work better.  But with two drives that is not an issue. And most just boot from the Ubuntu drive and use grub to boot Windows. You do not need EasyBCD then but can have it.

---

### Post by sjjubb1989 on 2012-05-12
Well my problem is definitely not with Windows or Ubuntu, but either with Grub or my computer itself. Grub will see ONLY the first drive that is plugged in, despite whether or not Grub is installed on the first or second drive. I switched my Windows dive and my Ubuntu drive to different slots in my computer, and if I boot into Grub using my entry from Windows Menu selection,, then it will load the Grub MBR and immediately go into rescue mode because it can't find my device. If I boot off of my Ubuntu drive, then Ubuntu will load but Grub's Windows entry will not boot because it can't find the device. I have done everything possible that I can think of short of copying my Windows boot sector and linking the file to grub from /boot to try booting Windows, because it seems Grub refuses to see any hard drive but the first one on my SATA setup. I've switched my drives around to many configuration for the 5 supported SATA devices, and only the first one is ever seen.

---

### Post by oldfred on 2012-05-12
With SATA drives you set which drive is the boot drive in BIOS. There also should be a one time boot key (f12 on mine) that lets you choose boot device as as BIOS is loading.

 Some computers have the choice of boot drive with the choice of boot device (CD, hard drive, USB etc) as  a sub menu under hard drive, and others have it totally as another entry even on a different BIOS page.

Some Dell's require you to both set BIOS and change one time boot key.

---

