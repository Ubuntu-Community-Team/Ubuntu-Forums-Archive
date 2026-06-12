---
title: "Messed up a friends PC. How to remove grub and restore mbr?"
date: 2011-06-27
forum: General Help
---

### Post by Keypel on 2011-06-27
My friend wanted to try ubuntu so I installed it on a usb hard drive thinking it would be safe. Unfortunately ubuntu wrote grub to the main hardrive without prompt.

for whatever reason, ubuntu is not running off the usb hdd so I unplugged it. Now grub is trying to find the missing hdd and is at grub rescue.

I know I installed ubuntu to the correct hdd so my friends data should still be fine on the main hdd, right? I just have to fix the mbr so that Win7 boots agian.

Thank for any help in advance.

---

### Post by TeoBigusGeekus on 2011-06-27
Try [this]("http://windows7forums.com/windows-7-support/34709-how-remove-grub-loader-get-windows-7-boot-loader-back-uninstalling-linux.html#post129181").

---

### Post by Keypel on 2011-06-27
Thanks of the reply. Your link probably would have worked accept I made a small mistake in my description above. The main hdd had Vista not Win7 on it.

I tried to fix the mbr with a Win7 but that's not going to work and I don't have access to Vista disc.

---

### Post by oldfred on 2011-06-27
It is the same MBR for Vista & 7. Actually any windows MBR will work, the main differences with XP & Vista/7 is in the PBR or partition boot sector.

You can install lilo's boot loader to the MBR from a Ubuntu liveCD. It works just like a windows boot loader in that it just looks for a partition with the boot flag and jumps the the PBR of that partition for more boot code. You do not install lilo's boot code to a PBR, but leave windows code there.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. 
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

If you can boot the external & lilo info:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If that does not work, you may have other issues. Then we will want boot script.

---

### Post by Keypel on 2011-06-28
Thanks for the reply old fred.

This is turning into a bit of a mess.

I found a vista disc but the disk has no repare options or bootrec.

Then I downloaded a vista restore disc but it complains that the version doesn't match the installed OS.

I read your link about no boot without external drive. The HP computer in question won't run ubuntu at all. not on a usb drive and not as a live CD.

Now as a last resort, I'm going for the lilo option. I'm going to have to pull the drive out and put it into an enclosure so that I can work with it on my ubuntu system.

I'm tired, I'm going to sleep on it. I don't want to do anything stupid when I'm tired and frustrated. Only the mbr is messed up at this point. I'm sure all my friends data is still safe on the rest of the hdd.

The alt Ubuntu always asked if it was ok to write grub to sda or not. The regular Ubuntu did not ask, I would have answered no. I already had the bios set to boot my hdd of choice. There was no reason to write to sda. Errrrrr.

---

### Post by oldfred on 2011-06-28
You can use a liveCD of just about any Linux. A lot of the Linux repair CDs have Lilo already installed or other ways to install a windows boot loader.

Ubuntu seems to assume that if you are using the auto install, you only have one drive and want grub2's boot loader in sda. With more than one drive whether internal or external or USB flash you need to use manual install so you  get the combo box that lets you choose to install to the MBR of the drive you install into.

Installing Ubuntu in Hard Disk Two (or more) Maverick 10.10
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by Keypel on 2011-06-28
old fried

I read and re-read some of the links you provided above

> On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
 Then click on "Command prompt". From there, type in the folowing:

UNSELECTING did the trick.

The Day is Saved.

---

