---
title: "Small Bootable Grub Rescue CD"
date: 2012-03-27
forum: General Help
---

### Post by Graham1 on 2012-03-27
Hi

Are there any small bootable Grub2 rescue CD's available that I could use to restore Grub should I run into any problems. The ones I have seen so far are 300MB+. 

I'm not much of a terminal user so ideally something with a simple GUI. I would imagine such a tool would only be a couple of MB's.

:)

---

### Post by oldfred on 2012-03-27
If you want a gui.

Boot Repair but LiveCD is based on Ubuntu so is larger:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

Some versions are smaller:
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)

But the new grub 1.99 wants you to use the same version of grub2  to reinstall with the simple two line reinstall commands. I think a full chroot will still work but that is certainly not gui base.

You can also create liveCD or USB that just boot. That would bypass grub issues, but not other install issues.

Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

Herman has instructions for grub2 rescue boot CD, USB, or floppy. Also grub legacy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM")

And these scripts automate the install of multiple bootable ISO onto one USB.
This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
multicd.sh - combine Linux ISOS into one 
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

Some suggest having several like these on one CD or USB.
Parted magic, gparted, any live linux, supergrub

---

### Post by Mark Phelps on 2012-03-27
+1 for SuperGrubDisk.  Been a while since I had to use it, but when last I did, it easily fit on one of the small 210MB mini-CDs.

---

