---
title: "help - I've fdisked it up"
date: 2011-12-22
forum: General Help
---

### Post by Bini_1 on 2011-12-22
I used the GUI tool to change the mounts and it seems to have done more than I expected. The machine will no longer boot.  When I get it started from a live disk, fdisk -l shows none of the partitions flagged as bootable.  It looks like the partitions are still there and correct.  When I mount the disk the /boot directory looks to be still in tact.  How do I flag an existing partition as bootable without changing the partition in any other way ?

---

### Post by MartijnNL on 2011-12-22
The a command in fdisk sets the bootable flag. But I don't think that's the issue as GRUB doesn't need the flag if it's installed in the MBR (which is the default). I think you changed your partitions in such away that the GRUB (bootloader) configuration is not correct anymore.

What changes do you mean with "change the mounts"?

I would try booting using [SuperGrub2Disk]("http://http://www.supergrubdisk.org/super-grub2-disk/") and then running sudo update-grub once you're in your system.

---

### Post by BC59 on 2011-12-22
Another solution would be to boot from a Live CD and install the Storage Device Manager. Then open it and change the options of the partitions to default.

---

### Post by BC59 on 2011-12-22
Then of course use the Live CD to reinstall Grub
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Bini_1 on 2011-12-22
I had a second disk that was wired up but the partition on it was not mounted.  I just added a mount point for it using some disk utility.  The entries in fstab look unchanged from a backup I made of it some months ago.  Am I looking in the right place ?  I'll have a look at the menu.lst and see what grub thinks the boot partition is.  Thanks

---

### Post by BC59 on 2011-12-22
Why don't you try to reinstall Grub according to my post#4?

---

### Post by Bini_1 on 2011-12-22
I'm in a bit of a mess  
The only live CD I have is Ubuntu 9, the installed version is 10.4.  The only way I have of burning CDs is a windoze XP laptop - these CDs are then not bootable on the Ubuntu machine for some reason.  So I couldn't get the boot-repair working.

---

### Post by BC59 on 2011-12-22
Why don't you use a USB? You can make it bootable with Unetbootin for Windows and you can use any .iso you like.

---

### Post by Bini_1 on 2011-12-23
My hardware is too old, I can't boot off USB devices 
 
I did try to chroot to the installed version and update-grub, but it said it couldn't resolve the UUID for the drive
 
 Not sure if that is due to chroot, or the real cause of the problem

---

