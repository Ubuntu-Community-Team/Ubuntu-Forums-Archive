---
title: "Grub2 Message"
date: 2009-11-17
forum: General Help
---

### Post by Quarkrad on 2009-11-17
When Grub2 installs itself I get this output from terminal:

[B]Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/Audio: No such file or directory
ls: cannot access /media/Audio: No such file or directory
Found Windows NT/2000/XP (loader) on /dev/sda2
done[/B]

I can access my three* winxp partitions via the Windows NT/2000/XP link at the bottom but I'm a bit confused with the two lines:

[B]ls: cannot access /media/Audio: No such file or directory
ls: cannot access /media/Audio: No such file or directory[/B]

* The three winxp partitions are called Dad, Audio Dad  and Multimedia (these are the ones I access via the **Windows NT/2000/XP (loader) on /dev/sda2** link.  In nautilus I can see these ntfs partitions as media/Dad, media/Audio Dad and media/Multimedia.  Why is grub trying to find media/Audio and what is it (media/Audio Dad?)?

---

### Post by blueridgedog on 2009-11-17
The new grub builds the boot menus automatically and finds bootable OS's without the need to configure them.  I believe you can ignore the error as there is no boot information on the partitions you mention.

---

