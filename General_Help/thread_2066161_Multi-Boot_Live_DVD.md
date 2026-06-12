---
title: "Multi-Boot Live DVD"
date: 2012-10-03
forum: General Help
---

### Post by SaiyanEye on 2012-10-03
Can someone point me into the right direction to making a multi-boot live DVD?

For instance,

Ubuntu 32bit
Ubuntu 64bit
Mint 32bit
Mint 64bit

All on one DVD

Could I use Grub on a DVD or a similar bootloader?

---

### Post by raja.genupula on 2012-10-03
you can find the information here
[http://www.webupd8.org/2010/02/multicd-builds-multi-boot-cd-dvd-with.html](http://www.webupd8.org/2010/02/multicd-builds-multi-boot-cd-dvd-with.html)

---

### Post by oldfred on 2012-10-03
Basic grub or grub2 rescue CD.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)

I think this is the same as raja.genupula's link.

cd/dvd ---------------------------------------------------------------------
[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

CD/DVD multiboot
multicd.sh - combine Linux ISOS into one - syslinux boot loader or isolinux.cfg 
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://multicd.tuxfamily.org/](http://multicd.tuxfamily.org/)

How to create an Ubuntu All-in-one Live DVD uses grub4dos
[http://prshah.blogspot.com/2009/10/how-to-create-ubuntu-all-in-one-dvd.html](http://prshah.blogspot.com/2009/10/how-to-create-ubuntu-all-in-one-dvd.html)

Older but procedure is same.
[http://askubuntu.com/questions/28299/dvd-with-both-32-bit-and-64-bit-ubuntu](http://askubuntu.com/questions/28299/dvd-with-both-32-bit-and-64-bit-ubuntu)

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)


But I prefer USB flash drives as then you boot with grub2 and just copy ISO to flash drive. Then when updates to ISO occur you can just copy new ISO and minor edit of grub.cfg for version change.

These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)

---

### Post by prshah on 2012-10-04
> **SaiyanEye said:**
> Can someone point me into the right direction to making a multi-boot live DVD?

Hi, please see [http://prshah.blogspot.com/2009/10/ive-been-trying-to-make-ubuntu-all-in.html](http://prshah.blogspot.com/2009/10/ive-been-trying-to-make-ubuntu-all-in.html)

Please post back here with questions / doubts, if any.

---

