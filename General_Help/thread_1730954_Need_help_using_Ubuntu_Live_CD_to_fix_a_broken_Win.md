---
title: "Need help using Ubuntu Live CD to fix a broken Windows Installation"
date: 2011-04-16
forum: General Help
---

### Post by shinkaide on 2011-04-16
Hi guys, I wasn't sure where to put this, so...

I'm currently trying to use an Ubuntu live cd to access and maybe fix a broken Windows XP laptop for a relative. It's my first time trying to do something like this after reading about it on lifehacker, and I've had a bit of success so far. I was able to save all her important files to an external hard drive.

But now I need to gather hardware information about her computer so I can reinstall Windows XP (she's not very comfortable with Ubuntu yet), but I'm not exactly sure how to do this. I've tried searching google, but I must be using the wrong keywords or something as I can't seem to find what I'm looking for.

Any suggestions?

---

### Post by PCaddicted on 2011-04-16
Install Ubuntu instead of Windows,it is much better.You won't need to format the hard drive before starting the installation of Ubuntu.

---

### Post by Ad@m on 2011-04-16
If you have a working net connection on the Ubuntu Live CD, install hardinfo.

sudo apt-get install hardinfo

Then run the application,

Applications > System Tools > System Profiler and Benchmark

you could also try running CPU-Z in Windows, [http://www.cpuid.com/softwares/cpu-z.html](http://www.cpuid.com/softwares/cpu-z.html)

---

### Post by marin123 on 2011-04-16
```
lspci
```

will tell you names of most components inside: graphic card, network controllers, sound card, etc...

i did that once and i managed to find all drivers...

---

### Post by shinkaide on 2011-04-16
> **PCaddicted said:**
> Install Ubuntu instead of Windows,it is much better.You won't need to format the hard drive before starting the installation of Ubuntu.

You have a reading comprehension problem, my friend.

---

### Post by shinkaide on 2011-04-16
> **Ad@m said:**
> If you have a working net connection on the Ubuntu Live CD, install hardinfo.

sudo apt-get install hardinfo

Then run the application,

Applications > System Tools > System Profiler and Benchmark

you could also try running CPU-Z in Windows, [http://www.cpuid.com/softwares/cpu-z.html](http://www.cpuid.com/softwares/cpu-z.html)

> **marin123 said:**
> ```
lspci
```

will tell you names of most components inside: graphic card, network controllers, sound card, etc...

i did that once and i managed to find all drivers...

Thanks a lot, fellas! Those two are a big help!

---

### Post by oldfred on 2011-04-16
If XP just needs some fixes to boot, that can all be done from Ubuntu, except chkdsk. Chkdsk can be run from any windows repair CD (XP/Vista/7).

XP CD fixboot 
[http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html](http://www.ehow.com/how_4891476_reinstall-xp-bootloader.html)
Description of the Windows XP Recovery Console for advanced users list of commands
[http://support.microsoft.com/kb/314058/](http://support.microsoft.com/kb/314058/)
To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type commands one at a time.

FIXMBR  C:  #do not run if you still want grub in the MBR
FIXBOOT  C:
BOOTCFG  /rebuild  # rebuilds boot.ini
chkdsk c: /r

COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
Where [CDDrive] is location of cd or D: etc.

or:
Can you boot into Ubuntu? If so you can mount your Windows drive and navigate to C:\windows\ServicePackFiles\i386 folder and copy
ntdetect.com and ntldr to root of C:\. 

How to fix XP/Vista/7 when the boot files are missing meierfra
[http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4](http://ubuntuforums.org/showthread.php?p=5726832#post5726832#4)

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing testdisk with Synaptic.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR

---

### Post by K_45 on 2011-04-16
I'll chime in and say use Ubuntu, specifically Xubuntu if that system is lower specced. XP, like IE6, needs to dies as soon as possible. It is a decrepit, insecure OS.

---

