---
title: "Quick partitioning question"
date: 2010-05-08
forum: General Help
---

### Post by Scooter_X on 2010-05-08
Yea, so I'm about to install 10.04, I just re-did my partitions from a dual-boot. I'll be ONLY running ubuntu. So far I have set up as follows, with PLANS to make sda3 my /home partition.

/dev/sda
[INDENT]/dev/sda1  ext4     /
/dev/sda2  swap
/dev/sda2 ext4    /home (this partition has data on it that I don't want lost)
[/INDENT]SO, It's already ext4, and when I go to select it and tell it 'ext4' and for the mount point to be /home, it's not supposed to erase anything, yea? I mean, I know there's a risk, but if it's too huge, I'll wait until I can get my hands on an external hard drive so I can be safer about it.

---

### Post by DJ_Max on 2010-05-08
Technically you're are doing a clean install on / but than an upgrade on /home. I've never had much luck completing upgrades on Linux, this is one area it fails miserably.

You should have backups of your data regardless, especially if they mean anything to you. If you dont check "format" for /home than it will not touch it. 

But remember you have configuration files on /home that will need to be updated manually

---

### Post by zacktu on 2010-05-08
Don't click the "Format" cell for /dev/sda2.  After you have finished defining partitions and click "Forward", the installer will list for you the partitions that will be formatted.  At this point you can still abort the installation if it's not going to format partitions as you want it to.

---

### Post by john newbuntu on 2010-05-08
You've mentioned sda2 twice.  I think the second is supposed to be sda3.
Make sure that during installation you DO NOT choose formatting.  Otherwise everything will be wiped clean.  Once again you need to go to the manual partitioning scheme and for the /home partition, point it to /dev/sda3 but uncheck format checkbox.  That should do it.  But always a good idea to make a backup of /home using perhaps tar or any other means that you are familiar with.

---

### Post by Scooter_X on 2010-05-08
Thanks guys. I'm backing up all my photos right now and some stuff for school. Everything else (all 50 gigs of it) is expendable. Who knows why I have so much stuff that I'm not worried about but that matters so much? I need to go through my stuff and sort it all out!! Well, I guess I have tons of music too... But I've got all of it on CDs. Anyways, I'll just make sure and keep the 'format' box cleared. Thanks again!

):P

---

### Post by QLee on 2010-05-08
[QUOTE=DJ_Max]Technically you're are doing a clean install on / but than an upgrade on /home. I've never had much luck completing upgrades on Linux, this is one area it fails miserably.[/QUOTE]

Perhaps you personally haven't been successful upgrading but I have to take exception with your statement as it stands. Maybe you are just referring to your experience with Ubuntu. The Linux Kernel (which is used on many distros) does not fail to upgrade. And I have had personal experience with lots of upgrades to a new version of a GNU/Linux distro., even Ubuntu. The times I had trouble were the times I did not read the "release notes" previous to trying the upgrade.

[QUOTE=DJ_Max]You should have backups of your data regardless, especially if they mean anything to you.[/QUOTE]

Good advice.

[QUOTE=DJ_Max]But remember you have configuration files on /home that will need to be updated manually[/QUOTE]

Perhaps some might, however, most (if not all) can be upgraded when the package manager configures the package. Assuming you follow a sensible upgrade path (i.e. one version step or LTS->Lts)

---

### Post by DJ_Max on 2010-05-08
I should have clarified, I meant Linux distros, not the Linux kernel itself

---

### Post by efflandt on 2010-05-08
Yes, it is best to test from an external drive if in doubt.  I installed 10.04 LTS with its grub on a USB hd.  It worked fine booting from 2 laptops, but would not boot from my desktop.  By default 10.04 aligns partitions differently, which is apparently incompatible with my older Asus motherboard (HP a530n from 2004).

It works after partitioning the USB drive from 9.10 and using the kernel boot parameter partman/alignment=cylinder listed in the 10.04 LTS Release Notes.  However, I checked the box to replicate my personal things from 9.10 on my internal hard drive to the USB drive, and 10.04 did not bring anything over at all.

I also ran into a post about a potential issue with Logitech Bluetooth keyboard and mouse, because 10.04 changed something that had been working for most of us to something that did not.  The change might make it impossible to even install 10.04 LTS using some Logitech devices like my diNovo Edge keyboard/mousepad, which is normally totally OS independent (works for BIOS password or CMOS setup, but stops working at 10.04 live/install menu).  Although, I do not use that all the time (to control a PC at a distance when connected to HDTV), I made sure that I had a solution (simply commenting out 2 lines in /lib/udev/rules.d/70-hid2hci.rules).  Some others with the problem did not have a wired keyboard handy to fix it.

---

### Post by QLee on 2010-05-08
[QUOTE=DJ_Max] should have clarified, I meant Linux distros, not the Linux kernel itself[/QUOTE]

I was just pointing out that the kernel is not the distro.

What I stated is still what I believe, there is no evidence that GNU/Linux distros will not upgrade correctly in general, although there might be troubles for some users, some specific hardware or upgrading a system to a new version when the old version was not yet fully upgraded. And I mean the config files in the users home too since the packager takes that into consideration.

---

