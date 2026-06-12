---
title: "Dual Boot:  1 Windows SATA hdd &amp; 1 Linux SATA hdd"
date: 2010-02-05
forum: General Help
---

### Post by cat2005 on 2010-02-05
I found several threads related to what I wanted to learn. I posted in one and was advised to create a new thread, since my situation is a little different.
 
In about 1 week I will get a new pc with 2 internal SATA hdds.
 
I want to have Windows XP on one and Linux Ubuntu on the other. 
 
My old system consisted of 2 internal IDE hdds. In that setup, this was my configuration:
 
a) 1st hdd: Windows XP and GRUB (old GRUB, not new GRUB)
b) 2nd hdd: Linux Ubuntu
 
I want to replicate that setup using the newer SATA hdds.
 
However, I read that GRUB does not play well if it detects 2 or more SATA hdds. Specifically, I read GRUB doesn't understand where to install, so it "guesses". 
 
Obviously, that is not acceptable.
 
I want to avoid complex solutions like chainloading. What are my options?
 
Thank you!

---

### Post by serpentracer on 2010-02-05
since I have a hp I can hold down escape during the bios flash screen and I can select which drive I want to boot.  (this is not it's setup where I change the boot order)
I'm not sure if other computers are like this now or it's just HP. It has a Asus motherboard.

other methods are with boot managers.
here is one for example...there are a bunch to choose from.
[http://gag.sourceforge.net/](http://gag.sourceforge.net/)

more,
[http://www.thefreecountry.com/utilities/multi-boot-managers.shtml](http://www.thefreecountry.com/utilities/multi-boot-managers.shtml)

---

### Post by cat2005 on 2010-02-08
> **serpentracer said:**
> since I have a hp I can hold down escape during the bios flash screen and I can select which drive I want to boot. (this is not it's setup where I change the boot order)
I'm not sure if other computers are like this now or it's just HP. It has a Asus motherboard.
 
other methods are with boot managers.
here is one for example...there are a bunch to choose from.
[http://gag.sourceforge.net/](http://gag.sourceforge.net/)
 
more,
[http://www.thefreecountry.com/utilities/multi-boot-managers.shtml](http://www.thefreecountry.com/utilities/multi-boot-managers.shtml)
 
 
Do you even use GRUB, or is GRUB not needed?

---

### Post by DestructionsRightHand on 2010-02-08
grub is still needed, on each hdd.  The way mentioned above is just picking the disk you want to boot from.  No way is the best, an alternative is to install them both on the same disk and set grub to pick the one you want to boot.  With grub two you can do this as you reboot, and use the second disk as a file store.

---

### Post by cat2005 on 2010-02-09
> **DestructionsRightHand said:**
> grub is still needed, on each hdd. The way mentioned above is just picking the disk you want to boot from. No way is the best, an alternative is to install them both on the same disk and set grub to pick the one you want to boot. With grub two you can do this as you reboot, and use the second disk as a file store.
 
 
So, to do it that way (where you go into BIOS and select which hdd), you need GRUB on both hdd.  Did I summarize correctly?
 
What if your BIOS does not have that boot option?  Would you just put GRUB on the 1st hdd?
 
Thank you!

---

### Post by oldfred on 2010-02-09
Computers boot from the first hard drive in BIOS, with old systems it was the first master in the IDE chain and the BIOS did not even control it. With SATA drives it is now all software controlled by the BIOS.

I think if you do a one time boot with F12 or whatever the BIOS still has the other drive as first. Grub will then still install to the drive BIOS has as first. There is an advanced button on the install about on the screen where you finalize partitions that lets you choose which drive to install grub to. It would be best to keep the windows boot loader on the windows boot drive and make the other drive first in BIOS to boot. Grub will install to that drive (check with advanced button) and find windows on the second. Grub will set up windows to think it is first so it still works, but if you want to switch drives back in BIOS you can still boot the windows drive.

---

### Post by oshunluvr on 2010-02-09
There's a couple of separate issues that you need to consider:

GRUB2 works well IF it's on the same drive as the boot partition you're booting to. The problem crops up when you put the boot partition on a different drive. I suspect this will be fixed soon, but as far as I know it still exists.

Solution 1: Don't install GRUB2 - use GRUB-PC (aka GRUB 1 or GRUB Legacy) or even LILO

Solution 2: Use GRUB2 and put both bootable partitions on drive 1! 

Steps for solution 2:
Download and burn GPARTED latest ISO
Using GParted:
  Partition the first drive:
    1st Primary: 1gb for linux swap area 1 
    2nd Primary: 400mb - use as **/boot** for ubuntu
    3rd Primary: Remaining for XP
  Partition the second drive:
    1st Primary: 1gb for linux swap area 2
    2nd Primary: 16gb for Ubuntu **/**
  The remaining amount divide up into logical partitions for data.

XP won't "see" the other primary partitions at all and will only access logical partitions if they are **fat** or **ntfs** formats. At the very least use a separate logical partition for **/home **and** /tmp**. You can read and write to NTFS from linux if you install the NTFS-3G packages so you can transfer and share data that way.

A separate **/tmp** will prevent over-filling your Ubuntu root partition with excess tmp data (thus making it un-bootable).

A separate **/home** makes your home data and settings safer (less likely to be lost if you re-install).

**Two swap partitions** will act as a small RAID0 device for linux making swap access faster if it is ever needed. Obviously, you can adjust the sizes I have suggested. You will need to add "pri=1" to both swap mount commands in **/etc/fstab** once you have Ubuntu up and running, but that's a real simple text edit.

Once you've partitioned both drives, make notes on paper as to what partition is for what. Then **install XP** to it's partition and boot it up to be sure it's working. Then install Ubuntu and select "Manual" at the partitioning stage and define the partitions as outlined above. Karmic will default to **ext4** which is OK if you want but I prefer **reiserfs** for now because **ext4** is still under development and has already shown some access time issues with the latest kernels. The bootloader (GRUB2) should automatically default to the first drive and detect your already present XP install. Since both boot partitions are on the first drive - GRUB2 should behave fine.

---

### Post by cat2005 on 2010-02-10
oshunluvr, oldfred,
 
If I want to stick with the old GRUB, then what are my options?
 
Thank you for your detailed answers!

---

### Post by oldfred on 2010-02-10
A new install of Karmic will install grub2 by default. All other older versions still use grub legacy. Grub2 is the future and at some point we all will have to convert as grub legacy has not been maintained for years and each distribution add tweaks to 0.97, Ubuntu added support in legacy 0.97 for ext4 but other distributions may have 0.97 and not work with ext4.

There are a few cases where grub2 does not work well, most of the issues are with learning a new way of doing things.

If you really want karmic but old grub:
Revert from grub2 to legacy grub - not a tutorial! 
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

---

### Post by oshunluvr on 2010-02-10
If you want to use the older version of GRUB, d/l **SuperGrubDisk** for GRUB Legacy and install it manually. You will likely have some learning to do if you're not familiar on the menu.list entries.

One thing I used to do on multiboot systems with GRUB Legacy was to use a dedicated GRUB partition rather than allow each distro to install its own GRUB. Most distros these days allow you to install GRUB to any partition you desire, rather than the main boot sector. In this manner, my dedicated GRUB partition and the main boot sector remained the same.

After each new install - I would edit the GRUB menu.list and manually copy the GRUB entries from the new distro into the "main" GRUB menu.list. The other advantage to this method is you were free to remove or re-install ALL your various distros and GRUB remained bootable.

For example - Steps to follow to do this:
1. Create small (500mb is plenty) primary partition on any drive.
2. Install distro of choice (ubuntu 9.04 would be a good choice) and install GRUB Legacy to main boot sector of first hard drive.
3. Copy all files from /boot/grub to the partition created in step 1.
4. Run GRUB and use the "root" and "setup" commands to direct GRUB to it's partition. 
5. Reboot to verify it works.
6. Install any number of distros - AND install their bootloaders to their INSTALL partitions, NOT the root partition.
7. Cut-and-paste menu.list entries (or create your own) for each of your distros in the GRUB partition's menu.list ad infinitum...

I will say - now that I've been playing around a bit with GRUB-PC (aka GRUB2) adding distros via update-grub has been WAY easier than with GRUB Legacy. I haven't yet tried to do the above with the new GRUB but I will eventually. I think it may be more difficult than before - but it will be a good challenge!

---

### Post by cat2005 on 2010-02-10
Wow, this is quickly getting confusing.
 
I would want this setup:
 
a) Windows on 1st SATA hdd
b) Ubuntu 9.04 on 2nd SATA hdd
 
I have SuperGRUB (old version, not new 2.0 version) cd so can use that if needed.
 
What is the simplest way to dual boot? I don't want to edit GRUB menus, etc unless doing so is unavoidable. Simplicity is the key.
 
_Questions_:
1) I could just put GRUB on the 1st SATA hdd, correct or not?  This is how I did dual boot with my dual IDE setup.
2) If my BIOS lets me select which hdd to boot, then all I would need to do is install GRUB on each hdd, correct or not?
 
Thanks!

---

### Post by oshunluvr on 2010-02-10
GRUB Legacy is known to have a little trouble with Windows installs sometimes - But it's not very hard to fix.

IMHO:
The "best" setup in this scenario is to install Windows to the SECOND hard drive. This allows windows installer to have the whole drive and use the master boot sectors. This also provides a little more security for you in that if you crash the linux drive - removing it and booting to the other drive will work and at least your windows install will be usable.

Then install Ubuntu (or any linux) and GRUB to the FIRST hard drive. 

To do this the "easiest" way (again IMHO) boot to and install Windows to the first hard drive. Then open the case and swap the drive cables (sata makes this real easy) OR use the bios to re-order the hard-drive boot sequence. Learning how to re-order your drives in bios is a good thing to know in case you run into problems later on.

Then install Ubuntu and GRUB-PC (rather than GRUB Legacy) to the other drive. 

GRUB-PC (aka GRUB2) will find the windows install and put it in your GRUB menu.

Set the GRUB/Linux hard drive as the first bootable drive. 

If you trash GRUB or this drive fails - simply re-order the drives in bios (or swap cables again) and you're booting windows again.


FYI: If your bios allows easy boot-order drive assignment, it really doesn't matter which physical drive holds which O/S. Windows will think it's on drive C: whether you boot it from GRUB or directly and it won't "see" your linux partitions at all. The point is to allow windows to "own" the boot sectors on it's drive so it's bootable as a stand-alone without GRUB at all.

---

### Post by cat2005 on 2010-02-11
> **oshunluvr said:**
> GRUB Legacy is known to have a little trouble with Windows installs sometimes - But it's not very hard to fix.
 
IMHO:
The "best" setup in this scenario is to install Windows to the SECOND hard drive. This allows windows installer to have the whole drive and use the master boot sectors. This also provides a little more security for you in that if you crash the linux drive - removing it and booting to the other drive will work and at least your windows install will be usable.
 
Then install Ubuntu (or any linux) and GRUB to the FIRST hard drive. 
 
To do this the "easiest" way (again IMHO) boot to and install Windows to the first hard drive. Then open the case and swap the drive cables (sata makes this real easy) OR use the bios to re-order the hard-drive boot sequence. Learning how to re-order your drives in bios is a good thing to know in case you run into problems later on.
 
Then install Ubuntu and GRUB-PC (rather than GRUB Legacy) to the other drive. 
 
GRUB-PC (aka GRUB2) will find the windows install and put it in your GRUB menu.
 
Set the GRUB/Linux hard drive as the first bootable drive. 
 
If you trash GRUB or this drive fails - simply re-order the drives in bios (or swap cables again) and you're booting windows again.
 
 
FYI: If your bios allows easy boot-order drive assignment, it really doesn't matter which physical drive holds which O/S. Windows will think it's on drive C: whether you boot it from GRUB or directly and it won't "see" your linux partitions at all. The point is to allow windows to "own" the boot sectors on it's drive so it's bootable as a stand-alone without GRUB at all.
 
 
oshunluvr,
 
Thanks again for the detailed response. So, to summarize:
 
a) If my BIOS allows easy boot order, then none of this matters. However, I would still install GRUB on each hdd. *Is that correct?*
 
b) Using the "Windows to 2nd hdd method" - Install Windows to 2nd hdd. Shut down and swap cables. Restart.  Then install Ubuntu & GRUB2 to the other hdd. *Using this approach, do I need to install GRUB onto the Windows hdd too?*
 
Thank you so much for your help!

---

### Post by oldfred on 2010-02-11
You do not need or want to install grub to both hard drives. Windows should be on its drive and grub on the Ubuntu drive. When you install windows it needs to be the first drive in BIOS so it installs its boot loader into the MBR of that drive. Then switch drives in BIOS so when you install ubuntu grub goes into the BIOS  for that drive. Each MBR has a different boot loader. When done the first drive should be Ubuntu as it will find windows, windows will not see the ubuntu partitions.

You can switch cables but on my system that only changes which is sda and sdb as that order seems to be the order plugged into the SATA ports. Changing that order after installing Ubuntu or windows may change some settings that would have to be updated. BIOS order chooses which drive boots first.

---

### Post by cat2005 on 2010-02-11
oshunluvr, oldfred,
 
Thanks so much!

---

### Post by oshunluvr on 2010-02-12
Oldfred and I are in agreement. You *could* use GRUB on both drives, but it's not the simplest or easiest way to do it. Another thing to note is a lot of new computers with dual drives are coming set up with BIOS based RAID aka Fake-RAID. You do not want this as it's a huge PITA and definitely NOT easy to work with.

Note though - if you have GRUB as your main bootloader - you should have a supergrub or livecd bootable linux disk around in case you mess up GRUB. Remember you won't be able to access your linux partitions from windows. It's not likely you would mess up GRUB unless you started playing with it or started installing other distros (Many new linux users jump around at first to see what other distros have to offer).

At this stage - I would recommended you use GRUB2 with your Ubuntu install. GRUB Legacy is on it's way out and is more difficult for a beginner. If you decide to start playing with additional installs - take some time to learn a little about updating and fixing GRUB *before* you start adding to your multi-boot.

Good luck! Let us know how it goes.

p.s.
Just because I'm bossy: I think you should consider partitioning your linux hard drive with five or six partitions. Why? I am assuming since it's a new computer your drives will be at least 250gb (likely 500gb) each. Linux doesn't need anywhere near that much space. Drive partitioning is way simpler with linux than it ever was with windows and it's harder to partition after you've installed everything.

Here's my suggestions - Download and burn a [GPARTED bootable iso]("http://sourceforge.net/projects/gparted/files/gparted-live-stable/0.5.1-1/gparted-live-0.5.1-1.iso/download"). Boot to it and do this:

BASIC PLAN:
Allow windows to use all of it's drive.
Linux drive only:

partition #1 (primary)- linux swap : usually suggested the same size as your total RAM. Personally, I think more than 2gb is unlikely needed but you'll have a ton of space so why not?

Remaining partitions are all logical (note: linux reserves partition number 1-4 for primary partitions so logical start at 5).

partition #5 - 16gb for Ubuntu **/**
partition #6 - all remaining space for** /home**
partition #7 - 16gb reserved for future or backup installs
partition #8 - 16gb same as #7
partition #9 - 20gb for** /tmp**

ADVANCED PLAN: 
Windows drive
partition #1 (primary) - linux swap : divide the desired amount of swap space and split it across both drives. Why? Because swapping to disk is way slower than using RAM, linux can use two or more swap partitions like a RAID drive (meaning faster than a single space).
partition #2 (primary) - for your windows install
partition #5  - some space for backing up data. Since you have two drives use some space to save your photos or emails or whatever. You can even set this up as an automated task later on.

You may also want to save some space on the windows drive for play with RAID later on. It much easier to reserve some space now than create some later.

---

### Post by cat2005 on 2010-02-12
oshunluvr, oldfred,
 
If it doesn't matter which hdd gets which OS, then does it matter which OS I install first? 
 
_Question_:
In other words, should I install Linux first or Windows first?
 
_Specs_ (I pick it up today):
- 4 GB system ram
- 1 GB nvida card
- 2x 160 GB internal SATA hdd (1 for Windows XP, 1 for Linux Ubuntu 9.04)
- Intel i3 @ 3.06 ghz
- Plan to start with 32 bit Windows and 32 bit Linux, but in the future may go 64 bit for either, or both, OSs, If I go 64 bit, it would be with a "newer" Windows and a "newer" Linux Ubuntu.
 
Relatedly, my previous dual IDE setup was this:
 
1st (Primary) HDD: Windows XP with GRUB 0.97 (Legacy)
2nd (Secondary) HDD: Linux Ubuntu 9.04
 
_Another Question_:
Legacy GRUB worked well in that setup. Shouldn't it work well if all I change is the HDD type (i.e., go from IDE to SATA)?
 
Thanks!

---

### Post by oldfred on 2010-02-12
If they are separate drives the installation order does not matter as long as for each drive you set that drive to first in BIOS so win or grub default to the install drive.

I also agree with oshunluvr on additional partitions as I created an extra partition for the next install so I could alternate, a separate /home and separte /data.

---

### Post by oshunluvr on 2010-02-12
I suggested doing windows first because GRUB will find it automagically and yes you can use GRUB Legacy - but GRUB2 is quickly developing and will soon be the standard.

ANY bootloader - even lilo (which I always liked better than GRUB Legacy) will do fine as long as YOU know how to set it up.

---

### Post by cat2005 on 2010-02-14
It worked!  Thank you both.

---

