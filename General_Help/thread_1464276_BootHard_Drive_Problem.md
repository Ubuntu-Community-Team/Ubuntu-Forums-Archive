---
title: "Boot/Hard Drive Problem"
date: 2010-04-28
forum: General Help
---

### Post by Me_Rock on 2010-04-28
Alright, my problem is somewhat hard to explain. I'll start from the beginning.

I'm setting up a home server/secondary workstation. It has three hard drives. I'll make a list, hopefully to simplify things.

sda: 500GB Samsung (Boot)
sdb: 500GB Samsung (Data)
sdc: 1000GB Seagate (Data)

The two 500GB drives are identical, but contain different data. The problem comes in when booting up. Whenever the two 500GB drives are both plugged in, Xubuntu 9.10 fails to boot. I can only get the OS to load when the second 500GB drive isn't connected.

I booted the live CD, to investigate the problem, (with all three drives attached) and fdisk -l finds all of the drives correctly. I later tried to reinstall the OS from the live CD, and it picked up the two 500GB drives as a RAID. I have RAID disabled in the BIOS, and both of the drives contain different data. Also, Gparted picks them up as separate drives.

So, what I think is happening is that when it's booting, and when I get to the partition manager in the install wizard, it tries to pretend that the OS disk is part of a RAID array. Again, everything works fine when the OS disk is on its lonesome or with the 1000GB drive. I have verified that it is not a power supply issue.

I'm baffled. Any input on the matter would be greatly appreciated

Thanks,
Me_Rock

---

### Post by Monkey77 on 2010-04-28
Sounds like you need to change the boot order in the BIOS.

Plug both in, go to the BIOS boot order and put the other HDD at the top.

I have two identical drives and the BIOS has the same name for both, however if I change the order they do boot in a different order.

---

### Post by varunendra on 2010-04-28
> **Monkey77 said:**
> Sounds like you need to change the boot order in the BIOS.

Plug both in, go to the BIOS boot order and put the other HDD at the top.

I have two identical drives and the BIOS has the same name for both, however if I change the order they do boot in a different order.
Agree. Most likely to be the reason.

If that doesn't solve it, how about installing without the 2nd drive, and connecting it after the installation is finished?

But frankly, boot-order seems to be the most obvious reason.

---

### Post by Me_Rock on 2010-04-28
> **varunendra said:**
> Agree. Most likely to be the reason.

If that doesn't solve it, how about installing without the 2nd drive, and connecting it after the installation is finished?

But frankly, boot-order seems to be the most obvious reason.

I've messed with the boot order on more than one occasion. That was in fact my first thought. I'll give it another go, but even so, there is nothing bootable on the conflicting drive. I've verified with Gparted that the only thing on the second drive is a non-bootable NTFS partition.

I think it has something to do with Ubuntu trying to autodetect a RAID that isn't there on bootup.

EDIT: Also, when it boots up, it gets started on loading up Ubuntu. Partway through it can't find where the root directory has gone or something.

Thanks again,
Me_Rock

---

### Post by varunendra on 2010-04-28
> **Me_Rock said:**
>  Also, when it boots up, it gets started on loading up Ubuntu. Partway through it can't find where the root directory has gone or something.
Me_Rock
I see! You didn't mention earlier that loading starts then fails partway.
Since I'm not so deep into linux yet so can only suggest some noob-like workarounds;). Just to make sure it is something wrong with the way Xubuntu is working, have you tried some other OS (Suse, CentOS,... maybe- Windows?) 
I'm assuming you should have some other OS discs lying around since you are playing with a potential server!
It'll take just a couple of hrs. to help zeroing out the root cause (is it the OS, BIOS, or hardware?)

Hope it doesn't sound stupid.:lol:

---

### Post by Me_Rock on 2010-04-28
> **varunendra said:**
> I see! You didn't mention earlier that loading starts then fails partway.
Since I'm not so deep into linux yet so can only suggest some noob-like workarounds;). Just to make sure it is something wrong with the way Xubuntu is working, have you tried some other OS (Suse, CentOS,... maybe- Windows?) 
I'm assuming you should have some other OS discs lying around since you are playing with a potential server!
It'll take just a couple of hrs. to help zeroing out the root cause (is it the OS, BIOS, or hardware?)

Hope it doesn't sound stupid.:lol:

I've tried Gparted from a liveCD and also Xubuntu from a USB drive. Both worked correctly and detected the hard drives individually.

Also, I just tried doing a low-level wipe of the OS drive and reinstalled Xubuntu. No dice. It has to be something with the way Xubuntu loads up. Is there some way that I can prevent it from seeing the drives as a RAID on boot up?

---

### Post by varunendra on 2010-04-28
Things are slightly different when you boot from external media. Most often they use isolinux instead of anything that is on HDD's MBR. And isolinux looks onto cd/usb drive for the kernel image rather than looking on HDDs. Hence easy to find, no confusion there.

So I just meant to try making a proper install of some other OS on the harddisk and let it boot through its own MBR, not from any external media like CD or USB. And yes do it with all HDDs connected.
Say, if you are able to install and boot Windows correctly, then we can say for sure that it is Xubuntu's fault. Otherwise the culprit lies somewhere else.

In all the previous failed attempts you made, there was one thing in common- the OS itself. Let's change it for a while and see what happens!

But again, I'd like to maintain that I'm not an expert. It's just my humble suggestion.

---

### Post by john newbuntu on 2010-04-28
Double check BIOS to make sure it is disabled.
In Karmic's release notes, there is a section called "Dmraid active by default on Desktop CD".  It suggests a method to disable it using F6 in the CD boot menu.
[http://www.ubuntu.com/getubuntu/releasenotes/910#Dmraid%20active%20by%20default%20on%20Desktop%20CD](http://www.ubuntu.com/getubuntu/releasenotes/910#Dmraid%20active%20by%20default%20on%20Desktop%20CD)

---

### Post by oldfred on 2010-04-28
Did these drives ever have raid installed. Drives seem to save hidden settings that interfere with the install. Do not run this if you have/want raid.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

---

### Post by Me_Rock on 2010-04-28
> **oldfred said:**
> Did these drives ever have raid installed. Drives seem to save hidden settings that interfere with the install. Do not run this if you have/want raid.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings

Hey, thanks! That was exactly what was wrong.

---

