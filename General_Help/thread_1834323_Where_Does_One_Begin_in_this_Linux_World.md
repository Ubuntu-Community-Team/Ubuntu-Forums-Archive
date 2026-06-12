---
title: "Where Does One Begin in this Linux World??"
date: 2011-08-27
forum: General Help
---

### Post by DigitalAdrenaline on 2011-08-27
Hi All, I am completely new to the world on Linux. And I mean completely new! I bought my first Linux magazine today and have been reading the web trying to get my head around all the jargon of distros, desktops, Gnome, Linux, Ubuntu etc etc, and how it all fits together. But my first few questions are really simple.
 
I'm running Windows 7 64bit now, Do I buy a whole new PC to install (Linux?)- I'm not sure what exactly. Or do I install it to a new external hard drive that's plugged into my current PC? If so, will the two operating systems have a nervouse breakdown competing with each other and not fire? 
 
How do I safely play with this Linux operating system while W7 is on my current PC? 
 
I'm sorry for being a real newbie, I'm just looking for some basic hesad's-up guidance. Appreciate any feedback guys. Many thanks.

---

### Post by nothingspecial on 2011-08-27
Hi, you don't have to buy a new pc.

You can use a bit of space on your current one for linux. The ubuntu installer will do that for you.

If you use an external hard drive, your computer will not boot unless it is plugged in. If that is not a problem then fine.

You can try it by booting from the cd. Give it a few hours and see if you like it.

If you are not sure about any steps in the installation just post here.

Back up all your important stuff first.

---

### Post by DigitalAdrenaline on 2011-08-27
Thanks nothingspecial. I'm inclined to load it to a spare external hard drive and keep that hooked to my main PC.  That being the case, do I just run the CD disk (from the magazine I bought) to the external hard drive and let nature take its installation course from there?  Cheers.

---

### Post by dino99 on 2011-08-27
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

and more below with the provided links :)

---

### Post by sanderd17 on 2011-08-27
> **DigitalAdrenaline said:**
> Thanks nothingspecial. I'm inclined to load it to a spare external hard drive and keep that hooked to my main PC.  That being the case, do I just run the CD disk (from the magazine I bought) to the external hard drive and let nature take its installation course from there?  Cheers.

If that CD you got from the magazine is the standard Ubuntu 11.04 installation CD (which I hope), than you can do two things:

Run the CD when your computer is running windows. This will open Wubi (Windows-Ubuntu installer) to install Ubuntu **INSIDE** windows. Just like a program that is installed. This has the advantage that it's easy to test and uninstall agian. But if you run it too long that way, it will become unstable. 

If you put the CD in your computer and reboot with the CD in it, than you will be taken to a "live" environment. That means that Ubuntu will run directly from the CD (without touching your hard disk). In the live CD, you have another installation program. With that installation program, you can install Ubuntu **NEXT TO** (or instead of) Windows. That means that Ubuntu will come on a new partition. So if you want to delete Ubuntu afterwards, you will need to repair your partitions as they were before (not so difficult, but more difficult than the Wubi uninstallation method).

If I were you, I would try Ubuntu with Wubi until the new version comes out (in October). And install the new version next to Windows.

---

### Post by nothingspecial on 2011-08-27
Boot it up.

Play with it for a bit. Check everything (sound, networking etc) works, which it should.

During the installation, you are going to have to choose "something else", assuming you are installing the latest version 11.04.

You have to be extremly careful during this bit. If you get it wrong you could wipe windows and all your data. Did I mention backing up?

After selecting "something else" during the install (you'll see what I mean when you get there), you will have to select which partition (drive) to install Ubuntu to. [COLOR="Red"][SIZE="3"]_You must get this right_[/SIZE][/COLOR]

Select to use it as an ext4 journaling file system.

In the dropdown box next to "mountpoint" select /

Choose to format it.

Do not touch the windows partition/drive

The issue is that the ubuntu installer will install the boot manager to the external hard drive. You will not be able to boot windows without it plugged in.

You do not need a great deal of space for Ubuntu (15-20 gigs). Ubuntu will see and access your files on your windows installation without a problem. I suggest you mess with the cd/dvd a little first and ask a few more questions if you are unsure of anything.

Also, I'll have to come clean. Until this week, I have never used windows and I have certainly never installed Ubuntu as a dual boot keeping windows. (I always overwrite it). So although I have a high post count and might seem to you to know what I'm talking about, in this case, I don't really. You may want to wait for other opinions.

---

### Post by DigitalAdrenaline on 2011-08-27
Cheers guys,  I really appreciate all your feedback.  I'll read through it all properly tomorrow and look forward to playing with it then.  I'm now off to bed, it's almost 1:30am.  Thanks all.

---

### Post by sanderd17 on 2011-08-27
Two more things:

[LIST]
[*]Make a backup: you don't want to lose any files because you clicked on a wrong button. I accidently erased windows the first time I installed it. The installer has become better since, but it's still possible to erase Windows.
[*]Defragment your disk at least two times before you change your partitions. This significantly reduces the chances of a failed installation.
[/LIST]

Btw, the Linux filesystem (ext4) doesn't get fragmented, so you wont find Linux defragmentation tools.

---

### Post by The Cog on 2011-08-27
As for installing to an external hard disk, take heed of the warning that if you do that then the PC will not boot without the external disk plugged in. It won't even be able to boot windows without the external hard drive plugged in. 

I agree that perhaps wubi would be good for a try-out, and if you like it, go for a proper dual-boot install that involves making room on th ehard disk for the Linux partitions, by shrinking the windows partition a bit.

---

### Post by oldfred on 2011-08-27
If you have a larger USB flash drive you can install to that. It is not real speedy as both USB port and flash drive are a bit slower, but it is very functional.

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

If you want a lot of detail with pictures, Herman's site has detail. It may be overkill for a new user, but if you want to know and understand details his is the site to go to for dual booting.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

aysiu's site is good for simple instructions - just follow these instructions and it will work.
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by walt.smith1960 on 2011-08-27
I agree with starting with a LiveCD or LiveUSB.  That will give you an idea about how Linux and your hardware get along.  Most machines just work, some have a solvable problem -WiFi is a common problem- and a few machines just don't want to know about Linux.  I've had decent luck with a USB stick but had a problem booting my main desktop.  I had to format the USB drive in Windows before it would boot on that machine, something to do with a modular BIOS.  The other two were fine with the USB factory format.   I've never had a LiveCD or LiveDVD not boot but CD/DVD is slower and won't remember any setting changes.  A USB stick is writable so will remember things like network names and such.  You may have to reset your machine's BIOS boot order.  Mine is set

[LIST=1]
[*]CD/DVD
[*]USB HDD (Boots with USB flash drives)
[*]Hard Drive
[*]Network
[/LIST]
My machine will look for devices with boot code in that order and will boot the first usable device it finds.

There are two ways to create a Live USB stick.  One is to use a program that is part of a liveCD, "Startup Disk Creator" to create a bootable USB stick.  I've had better luck with Unetbootin, which is available for Linux or Windows so you can create a bootable USB drive in Windows.  Unetbootin is found here:

[http://en.sourceforge.jp/projects/sfnet_unetbootin/downloads/UNetbootin/549/unetbootin-win-549.exe/](http://en.sourceforge.jp/projects/sfnet_unetbootin/downloads/UNetbootin/549/unetbootin-win-549.exe/)

You can download that in Windows, do the "click on the .exe to install" routine.  Unetbootin can find and install common Linux operating systems onto your USB drive or you can download an .iso file and point Unetbootin toward that .iso to install it.  As long as your Windows partition is intact you're not under any pressure and can learn Linux at your leisure.  I assume there are functions that work with a hard drive install but not with a LiveUSB install but I don't know what they are -- perhaps printers?  Once you're confident in Linux you can install it in parallel with Windows.  It didn't take me long to put Windows "on the top shelf in the back of the pantry."  I have a couple things that I can't do in Linux but 95% of my time is spent in Linux.  I hope this makes sense to you.

---

### Post by YesWeCan on 2011-08-27
> **DigitalAdrenaline said:**
> Hi All, I am completely new to the world on Linux. And I mean completely new! I bought my first Linux magazine today and have been reading the web trying to get my head around all the jargon of distros, desktops, Gnome, Linux, Ubuntu etc etc, and how it all fits together. But my first few questions are really simple.
 
I'm running Windows 7 64bit now, Do I buy a whole new PC to install (Linux?)- I'm not sure what exactly. Or do I install it to a new external hard drive that's plugged into my current PC? If so, will the two operating systems have a nervouse breakdown competing with each other and not fire? 
 
How do I safely play with this Linux operating system while W7 is on my current PC? 
 
I'm sorry for being a real newbie, I'm just looking for some basic hesad's-up guidance. Appreciate any feedback guys. Many thanks.
Hi there. Welcome to the wonderful world of linux. :)
I am a Windows 7 user. Once you have Ubuntu installed and booting you'll be fine - getting there has some gotchas you need to know about.

1. Ubuntu does not boot using the conventional MBR system. Instead it replaces your exiting MBR boot code with one that will not function unless the Ubuntu boot directory is present. It is not a good idea to install Ubuntu's boot loader MBR code to the disk that Windows is installed on (or rather the disk that it is normally booted from) because Windows uses the conventional MBR system.

This may not effect you much at first because the Ubuntu boot loader, called Grub, will add your Windows OS to its boot menu. But from time to time Windows may spot the rogue MBR code and repair it thus disabling your Ubuntu. Or sometimes certain Windows programs and laptop vendor programs will use some of the MBR area and kill grub, or vice-versa. And if you delete your Ubuntu partition or Ubuntu gets corrupted for any reason, Grub won't work and you won't be able to boot Windows.

2. The Ubuntu MBR code can be installed to any disk, not just the one that Ubuntu is installed on.

3. The Ubuntu installer does something very naughty...if you do not explicitly tell it which drive you want the MBR code installed to it will default to what it calls sda (Sata drive A) which is often your Windows drive!

So the best thing to do if you are not sure is to install Ubuntu to a separate drive from Windows and explicitly tell the installer to put the boot-loader on the Ubunut disk. As a belt & bracses precaution unplug your Windows drive while you install Ubuntu.


Some other gotchas:
4. Grub comes in two versions. An old version prior to Ubuntu 10.04 (maybe prior to 9.10) which is now called "Grub legacy" and has a version number <1.0. Then there is the new Grub called Grub2 with version numbers >1.0 but confusingly <2.0 (!) and this is the Grub you will have if you do a fresh install of 11.04. I mention this because there are many tutorials out there and some are for Grub-legacy and some are for Grub2 and they are not always clear about which they are talking about! Note that fedora and OpenSuSE still use Grub-legacy.

5. Ubuntu's quality is not the same for every version. Only the LTS (Long Term Support) versions are considered very reliable. The others are a mixed bag. 10.04 is the most recent LTS version. 12.04 will be the next LTS version. 10.10 is very good (which is why I use it) and 11.04 is a little* too* new for my taste.

6. Ubuntu and linux, in general, are no where near as forgiving as Windows. You can do really damaging things without being warned. This is also a benefit because you can do all sorts of powerful, useful things that Windows won't let you do.

7. Ubuntu and linux in general is not developed and quality controlled by one organisation. Ubuntu is a collection of other people's programs. The quality is mixed. When people talk about the reliability of linux they usually mean the linux kernel (the basic operating system - which does not include most of the stuff you play with like the Gnome desktop and the file manager and multimedia programs and so on). The kernel is like the engine of a car - it is a Ferrari engine - but it isn't the whole car and it is developed by a separate organisation from the rest of the car. Linux is not as homogeneous as Windows so different programs look very different and behave differently and have different quality and different documentation. Like a quilt. Many of the patches are excellent but it is a patchwork.



I use linux for almost everything I do now but I still depend on Windows for some applications. I can do so much more with linux than I could with Windows but there is a learning curve. Although Ubuntu is free you don't get something for nothing. ;)

Good luck and have fun.

---

