---
title: "GRUB no such device without external USB"
date: 2010-08-17
forum: General Help
---

### Post by el_basto on 2010-08-17
Hi folks, so this is my problem:
I recently did an installation of ubuntu 10.04 on an external USB drive. I can no longer boot into my normal installation (on my hard drive) unless the USB stick is plugged in!

If I try to boot my computer with the usb stick *not* plugged in, I get the following error in grub rescue: no such device 24909fa4-90f1-49a2-96e9-bffc7e3522b4.

If I plug in the usb drive, I get my normal boot menu from which I can choose my normal (hard drive) ubuntu install. 

blkid, with the USB drive plugged in, gives: 
```
/dev/sdb1: LABEL="Data" UUID="52b274e3-84ca-443c-a4ec-95286b813bad" TYPE="ext4" 
/dev/sda1: UUID="b57769d3-4b12-4ab7-bb9f-ba4f6c86eb53" TYPE="ext4" 
/dev/sda3: UUID="000553e3-d30d-4cca-8395-a7767755a0ed" TYPE="ext3" 
/dev/sda5: UUID="6ed3dc94-aa09-462c-ac23-f85c2f74ad25" TYPE="swap" 
/dev/sdc1: LABEL="ViajeroData" UUID="E6AE-F7FC" TYPE="vfat" 
/dev/sdc2: UUID="24909fa4-90f1-49a2-96e9-bffc7e3522b4" TYPE="ext4" 
```blkid, with the usb drive unmounted and removed, gives:
```
/dev/sdb1: LABEL="Data" UUID="52b274e3-84ca-443c-a4ec-95286b813bad" TYPE="ext4" 
/dev/sda1: UUID="b57769d3-4b12-4ab7-bb9f-ba4f6c86eb53" TYPE="ext4" 
/dev/sda3: UUID="000553e3-d30d-4cca-8395-a7767755a0ed" TYPE="ext3" 
/dev/sda5: UUID="6ed3dc94-aa09-462c-ac23-f85c2f74ad25" TYPE="swap"
```so clearly the  /dev/sdc2 is the usb drive, and of course it makes sense that grub can't find it if it is not plugged in. 

I have already removed the drive and then ran update-grub (with no USB stick plugged in) but this does not resolve the issue. At this point I can't boot unless the usb stick is plugged in... any help?

---

### Post by alphaamanitin on 2010-08-17
> **el_basto said:**
> Hi folks, so this is my problem:
I recently did an installation of ubuntu 10.04 on an external USB drive. I can no longer boot into my normal installation (on my hard drive) unless the USB stick is plugged in!

If I try to boot my computer with the usb stick *not* plugged in, I get the following error in grub rescue: no such device 24909fa4-90f1-49a2-96e9-bffc7e3522b4.

If I plug in the usb drive, I get my normal boot menu from which I can choose my normal (hard drive) ubuntu install. 

blkid, with the USB drive plugged in, gives: 
```
/dev/sdb1: LABEL="Data" UUID="52b274e3-84ca-443c-a4ec-95286b813bad" TYPE="ext4" 
/dev/sda1: UUID="b57769d3-4b12-4ab7-bb9f-ba4f6c86eb53" TYPE="ext4" 
/dev/sda3: UUID="000553e3-d30d-4cca-8395-a7767755a0ed" TYPE="ext3" 
/dev/sda5: UUID="6ed3dc94-aa09-462c-ac23-f85c2f74ad25" TYPE="swap" 
/dev/sdc1: LABEL="ViajeroData" UUID="E6AE-F7FC" TYPE="vfat" 
/dev/sdc2: UUID="24909fa4-90f1-49a2-96e9-bffc7e3522b4" TYPE="ext4" 
```blkid, with the usb drive unmounted and removed, gives:
```
/dev/sdb1: LABEL="Data" UUID="52b274e3-84ca-443c-a4ec-95286b813bad" TYPE="ext4" 
/dev/sda1: UUID="b57769d3-4b12-4ab7-bb9f-ba4f6c86eb53" TYPE="ext4" 
/dev/sda3: UUID="000553e3-d30d-4cca-8395-a7767755a0ed" TYPE="ext3" 
/dev/sda5: UUID="6ed3dc94-aa09-462c-ac23-f85c2f74ad25" TYPE="swap"
```so clearly the  /dev/sdc2 is the usb drive, and of course it makes sense that grub can't find it if it is not plugged in. 

I have already removed the drive and then ran update-grub (with no USB stick plugged in) but this does not resolve the issue. At this point I can't boot unless the usb stick is plugged in... any help?

Sounds like you damaged the MBR on the internal hard drive.  This might be solved by using something like SuperGrub to reinstall grub on the internal drive.  

AlphaA

---

### Post by el_basto on 2010-08-17
I guess that what is telling is that GRUB keeps looking for the usb drive, is there a way to manually tell GRUB which drives to look for?

---

### Post by el_basto on 2010-08-17
Bit of an update: So I removed and reinstalled grub using the Software Center (gosh, that sounds so... so... so windows), then after reinstalling I ran update-grub with the usb drive removed and things work fine. However, now I can't boot into my thumb-drive! That is, if I choose "USB Device" from my BIOS boot menu, the computer now hangs. Any ideas? Perhaps I need to reinstall GRUB on the usb drive.

---

### Post by rakiim on 2010-08-17
hello, i have a problem with my laptop...I installed ubuntu and when I opened it appears that
error: no such device: c631ca9c-94e9-44c7-a0f9-f2ca5e33d9bf
grub rescue>

What can I do to not appears? I do not recognize any optical drive a CD or DVD


thank you.

---

### Post by alphaamanitin on 2010-08-17
> **el_basto said:**
> Bit of an update: So I removed and reinstalled grub using the Software Center (gosh, that sounds so... so... so windows), then after reinstalling I ran update-grub with the usb drive removed and things work fine. However, now I can't boot into my thumb-drive! That is, if I choose "USB Device" from my BIOS boot menu, the computer now hangs. Any ideas? Perhaps I need to reinstall GRUB on the usb drive.


Yes you need grub installed on the usb drive to boot directly from it.  I have never had any success trying to boot from external drives without grub on it-I don't know if it is possible but I can't get it done.  

And yes, to manual tell grub where to boot from you hit 'e' in the grub menu and it gives you the option to edit the information.

---

### Post by oldfred on 2010-08-17
Instructions on removeable drive issue.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

---

### Post by alphaamanitin on 2010-08-17
> **rakiim said:**
> hello, i have a problem with my laptop...I installed ubuntu and when I opened it appears that
error: no such device: c631ca9c-94e9-44c7-a0f9-f2ca5e33d9bf
grub rescue>

What can I do to not appears? I do not recognize any optical drive a CD or DVD


thank you.


You really should not hijack other peoples thread for a separate problem.  This is very odd, to me at least.  You installed it on the internal drive right?  So, if I understand you correctly, you turn on your computer, it posts and boots, then grub loads drives to load ubuntu and give the error that there is no such device:  c631ca9c-94e9-44c7-a0f9-f2ca5e33d9bf?  This looks like a UUID of your internal HD.  I suggest you hit 'e' and look at exactly what grub is trying to load.    You should see a line similar to this:

kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda0 ro quiet splash


Except yours might have root=UUID=c631ca9c-94e9-44c7-a0f9-f2ca5e33d9bf.  



If I were you I would put in a Ubuntu Live CD and run the command: "blkid".  This should give you an output of what file systems are there and there UUIDs.  If you only have one HD you should have two things in the output.  One will be your HD partition with your OS installed on it and the other will be the swap partition.  note the /dev/XXX and the UUID of the partition with the OS installed, write these down.  You can then hit 'e' again at the grub menu and edit the boot to point at the appropriate device that you have the /dev/XXX for and the UUID.  



Some one may have a much more elegant solution to your problem though and this may not be a solution at all.  I am not that skilled in GNU/Linux.


AlphaA

---

