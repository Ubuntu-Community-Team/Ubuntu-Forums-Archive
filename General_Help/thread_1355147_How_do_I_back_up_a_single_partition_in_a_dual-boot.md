---
title: "How do I back up a single partition in a dual-boot?"
date: 2009-12-14
forum: General Help
---

### Post by Quarkrad on 2009-12-14
If one has a dual boot system with Ubuntu on the 1st partition - and for example winxp (or any OS) on the 2nd partition - then there is a problem backing up/imaging and restoring Ubuntu?  I have this scenario (including 3 other partitions) and for some reason the boot partition is on sda2 (the winxp partition).  So I have used Clonezilla to backup sda1 onto HD2 but when I restore Ubuntu (9.10) grub is all messed up and I cannot get into my PC.  Feedback, so far, suggests imaging/backing up the whole disk (hd1 to HD2) but I only want to backup ubuntu so when I try different things out and possibly mess up I can image back rather than re-install as I'm doing at the moment.  Is there no way I can backup and restore just sda1 (ubuntu 9.10) without having to do the whole HD?   Perhaps the issue is with dual booting rather than ubuntu.  I'm getting my head round ubuntu from winxp and I really like it - 9.10 has given me no problem at all - really really good.

---

### Post by howefield on 2009-12-14
I will load up Clonezilla later, but I think you can save grub by choosing it through advanced settings when loading the clonezilla "wizard"

You may have used the beginner menu when you imaged previously ?

---

### Post by synapsys on 2009-12-14
It sounds like you need to simply make sure grub is installed to the first hard drive.
Then you can boot to a live cd (ubuntu install cd) and have grub scan your hard drives and automatically create a boot menu for you.

(in live cd)
Open Applications >> Accessories >> Terminal
and type:

```
sudo update-grub
```

then reboot.

---

### Post by Quarkrad on 2009-12-14
I have just re-installed 9.10.  But I will try the backup restore again.  Yes - I did use the 'simple' option to save the initial image.  Perhaps I should have been more brave and used the advanced option.  Thanks for looking into this for me - any help appreciated.  I would like to be able to restore just sda1.  Note:  as I have re-installed than sda2 (winXP/ntfs) will still be my boot partition.  Any advantage in moving (how?) Grub to sda1?

---

### Post by Leppie on 2009-12-14
what do you mean by sda2 is your boot partition?
my sda2 is marked as bootable, but grub is installed in the mbr. doesn't really affect booting ubuntu (on sda6 for me).

---

### Post by synapsys on 2009-12-14
You can definately choose a single partition to back up in clonezilla.

If your only problem is with grub after re-imaging, you can use the super grub disk to fix this:

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Quarkrad on 2009-12-14
Sorry - I'm a bit (a lot?) of a newbie here.  sda2 shows as my boot partition - to be honest I'm not sure of the relationship between MBR (that I though was an independent sector of the disk where the boot instruction were - and the boot partition (mine is sda2).  Thinking about this - is it the case that if you partition the HD with say 4 partitions the PC has to know what partition has the MBR/boot instructions on it.  So is my mbr/Grub/boot instruction on partition no. 2 - sda2?  Is this what my machine means by saying sda2 is the boot partition?

At the moment I have re-installed 9.10 but there is no grub/winxp option.  Working out how to put winxp/sda2 into the grub2 menu.  Many thanks.

---

### Post by synapsys on 2009-12-14
You're mostly right. A bootloader (grub) is on the very first part of the first hard disk, before sda1, sda2, etc.... It contains a set of instructions for booting into an operating system. 

Grub stores it's configuration file on your Ubuntu / or root partition. Your 'boot' partition is the partition that holds the /boot folder. You will find the configuration file for grub is /boot/grub/menu.lst When you install Ubuntu, grub should 'automagically' detect all of your bootable partitions and make an entry for them in your menu.lst.

To add an entry manually, you will add the right lines to menu.lst. Always be careful when doing this and make a backup first, just in case.

Windows tends to complain when it's not on the first partition of the first hard drive, it can be tricky to add it to menu.lst

---

### Post by Quarkrad on 2009-12-15
Thanks - but is it not the case that there is no menu.lst in 9.10/Grub2?  If it were grub1 I do not think I would be so bad at this.

---

### Post by synapsys on 2009-12-15
It looks like with grub 2 they don't want you to manually edit the file. Simply run sudo update-grub to add all existing bootable partitions to the boot menu.

More here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by Quarkrad on 2009-12-17
At last I solved the problem - thanks to some help from Philinux.  Clonezilla to backup and restore.  Then follow **[http://www.ubuntu-inside.me/2009/06/...r-windows.htm](http://www.ubuntu-inside.me/2009/06/...r-windows.htm)**l to get grub2 / system back.

---

