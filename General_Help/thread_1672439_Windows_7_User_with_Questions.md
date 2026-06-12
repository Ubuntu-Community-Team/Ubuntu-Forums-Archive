---
title: "Windows 7 User with Questions"
date: 2011-01-20
forum: General Help
---

### Post by Belaidivh on 2011-01-20
I am interested in using Ubuntu alongside my current Windows 7 64bit OS, but before I download and install it, I would like to know a couple of things.

I plan to use the Windows Installer on the Ubuntu website, are there any dangers to installing Ubuntu this way.?

I would also like to know if there is any way to easily uninstall Ubuntu if I do not wish to keep it.

---

### Post by wilee-nilee on 2011-01-20
> **Belaidivh said:**
> I am interested in using Ubuntu **alongside** my current Windows 7 64bit OS, but before I download and install it, I would like to know a couple of things.

I plan to use the Windows Installer on the Ubuntu website, are there any dangers to installing Ubuntu this way.?

I would also like to know if there is any way to easily uninstall Ubuntu if I do not wish to keep it.

If you use the windows installer it will be a wubi install. It is not alongside but a file inside of windows. This sort of install is a good way to try it out, without doing any partitioning. After installing, watch the updates/upgrades in Ubuntu don't do any grub-pc or grub common upgrades. 

With this install method the MS bootloader is still in charge=in the mbr, a grub upgrade will leave you unbootable, easily fixed though. 

With Wubi it is a easy remove Ubuntu leaving the MS bootloader still in place.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by ubuntu27 on 2011-01-21
Using Wubi install is a good way to try out Ubuntu Linux, but keep in mind that the OS that is installed with wubi does now show its real full power and potential. 

Since wubi installs Ubuntu inside Windows' partition, it naturally inherits Windows' weakness. Notably, since Windows can "touch" Ubuntu, user errors and Windows virus can harm Ubuntu that is inside Windows. (Ubuntu or any other Linux is virtually immune to Virus).

Also, Ubuntu with WUBI install would be slower than real installation since it will be using Window's file-system (NTFS, FAT32, etc) instead of Linux file-system (many FS) that is substantially faster.

If you so far like what you see using Wubi, and want to keep using Ubuntu, a real Ubuntu installation is recommended.


Take your time, and enjoy the ride! :popcorn:

---

### Post by Bucky Ball on 2011-01-21
Download the LiveCD (Ubuntu ISO) Desktop AMD64 version, try Ubuntu from the CD (one of the options after you boot from the CD). If you like it, dual-boot with Windows 7. Make sure you have some free space after Windows install or partitions you don't mind losing to install Ubuntu to.

Neither Wubi or trying from the CD will give you the full experience re: speed and configuration possibilities ...

BACK UP!!! ... any data you don't want to lose. We all make mistakes!

---

### Post by Rubi1200 on 2011-01-21
> **Belaidivh said:**
> I am interested in using Ubuntu alongside my current Windows 7 64bit OS, but before I download and install it, I would like to know a couple of things.

I plan to use the Windows Installer on the Ubuntu website, are there any dangers to installing Ubuntu this way.?

I would also like to know if there is any way to easily uninstall Ubuntu if I do not wish to keep it.
Hi and welcome to the forums :)

Yes, essentially Wubi is a safe way to try another operating system.

Read the Wubi Guide already posted.

Also, see here:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

On a fresh install you need to lock the grub-pc and grub-common packages so as to avoid some recent issues (see the section in the main post just after the Permanent Fix on how to do this).

---

### Post by Blue Dolphin on 2011-01-21
> **wilee-nilee said:**
>  After installing, watch the updates/upgrades in Ubuntu don't do any grub-pc or grub common upgrades. 


bcbc also mentioned this thing in my thread. [http://ubuntuforums.org/showpost.php?p=10380129&postcount=2](http://ubuntuforums.org/showpost.php?p=10380129&postcount=2)

But I am not clear what you or he means here? Can you please explain and let us know what do we need to do to prevent this update/upgrade? And what else wee need to take care of?

PS: I am also installing ubuntu with Windows7 using wubi.

---

### Post by wilee-nilee on 2011-01-21
> **Blue Dolphin said:**
> bcbc also mentioned this thing in my thread. [http://ubuntuforums.org/showpost.php?p=10380129&postcount=2](http://ubuntuforums.org/showpost.php?p=10380129&postcount=2)

But I am not clear what you or he means here? Can you please explain and let us know what do we need to do to prevent this update/upgrade? And what else wee need to take care of?

PS: I am also installing ubuntu with Windows7 using wubi.

Look at post 5, last paragraph, look at link for locking the grub packages.

Also just let it install in C, it is easiest to deal with I believe if it is in the main windows partition.

---

### Post by Blue Dolphin on 2011-01-21
> **wilee-nilee said:**
> Look at post 5, last paragraph, look at link for locking the grub packages.
Yes I just saw that. :)
Thanks.

---

### Post by MARP1961 on 2011-01-21
You may not always be happy with just a 'wubi install'. You may eventually want to let Ubuntu loose on your hard drive. In this case you just might do something risky, rash or impulsive and it is possible to lose your Windows partition altogether! With this in mind, make sure you can reinstall windows 7 from scratch if need be. Do you have a full install disk? Will Windows allow you to burn a copy from the Recovery Partition? Find out before you do anything then get the best of both worlds with a dual-boot arrangement and seek advice in the Ubuntu forums on how to keep data separate from the system by having  separate 'Root' and 'Home' ext4 partitions.

---

