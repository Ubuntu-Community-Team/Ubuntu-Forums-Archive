---
title: "live ubuntu usb on ext3 partition"
date: 2009-12-17
forum: General Help
---

### Post by linuxhippy on 2009-12-17
I recently downloaded and burned the xubuntu 9.10 cd for x86 for the purpose of making a live usb from it.  Making a live cd on a single partition fat32 stick was easy with the live usb-creator that's included.  However, I had previously partitioned the stick in half so that half the usb flash was ext3 (where I wanted live xubuntu) and the other half was fat32.  So it seems like xubuntu wants a fat32 partition.  I copied the files to my hard drive, re-partitioned the stick to fat32 and ext3.  Then I copied all the xubuntu live usb files back to the ext3 partition.

How can I get the stick to boot into xubuntu?  I also want to bypass the menu that pops up asking about the language...I want it to assume the user wants English with no prompting.  How do I do this?

I was told in another forum to use either extlinux (in the syslinux tarball) or grub...I need help, though.

---

### Post by warfacegod on 2009-12-17
You'll have to go into the computer's BIOS. Make sure the drive is plugged in. Hit F1 or F2 or whatever button it is when your booting up. It will probably be on the manufacturor's Logo screen where it says Dell or Toshiba or whatever. Make sure booting from the thumbdrive is enabled (some computers can't do this), it's probably under Boot Options or a similar name. Next, in Boot Order, make the thumbdrive first. Save and exit. Your computer should boot into the liveCD.

This is just meant to be a general idea. Different computer manufacture's BIOS setup's can be... well, different.



As far as skipping language selection, I have no idea. I'm guessing it's more hassle than it's worth.

---

### Post by warfacegod on 2009-12-17
By the way, I don't think I've ever gotten a thumbdrive liveCD to work when there's more than one partition on it.

---

### Post by linuxhippy on 2009-12-17
You misunderstood.  My usb does boot as the Ubuntu usb-creator left it...but it's on a fat32 partition.  I repartitioned this drive and then put all the files the Ubuntu cd-creator put on the fat32 partition on my new ext3 partition.  I think extlinux or grub is now needed to boot this drive (I already had my BIOS set to go)...how do I boot it now?

---

### Post by warfacegod on 2009-12-17
I'm not sure but I don't think what your trying to do will work. I don't think the average computer BIOS can even read ext3. I think that is why the USB Creator formats as FAT32. I believe using FAT32 fools the computer into thinking the drive is a CD ROM. However, I have been wrong before. Why use ext3 at all, why not just leave it as FAT32?

Sorry I can't be more helpful otherwise.


If you have xubuntu then you already have Grub.

---

### Post by bodhi.zazen on 2009-12-17
> **warfacegod said:**
> By the way, I don't think I've ever gotten a thumbdrive liveCD to work when there's more than one partition on it.

You may have mulitple partitions on a USB. With large flash drives, i  mane an 800 Mb FAT partition and the rest a data partition.

> **linuxhippy said:**
> You misunderstood.  My usb does boot as the Ubuntu usb-creator left it...but it's on a fat32 partition.  I repartitioned this drive and then put all the files the Ubuntu cd-creator put on the fat32 partition on my new ext3 partition.  I think extlinux or grub is now needed to boot this drive (I already had my BIOS set to go)...how do I boot it now?

As far as I know, you have to use FAT for the usb-creator.

If you did a full install, you can use ext3/4 or what you wish.

---

### Post by linuxhippy on 2009-12-17
It can be done-I know that.  I just made a live usb of slax on an ext2 partitioned usb flash drive.  They include a script called liloinst.sh that does this.  I'm not sure how-but it works.  Slax is really stripped down.  I like xubuntu on live usb...I just want to get it working with an ext3 partition so that it is hidden from typical Win installs and won't get automounted.  The blank fat32 partition on the usb will.

I'll look into putting grub on the stick...I already tried with extlinux and got it to boot to a boot line.  Almost but no cigar.  It's supposed to start out with a grub menu, though-so if I put grub on there again it would have 2 grub menus....


EDIT: That liloinst.sh script is only for Slax.  I already tried using it on xubuntu and it does boot the usb but cannot find files.

---

### Post by warfacegod on 2009-12-17
[/QUOTE]As far as I know, you have to use FAT for the usb-creator.

If you did a full install, you can use ext3/4 or what you wish.[/QUOTE]

I understand that. Iwas under the impression that linuxhippy wanted to run a liveCD.

---

