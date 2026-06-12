---
title: "ubunutu boot"
date: 2012-05-06
forum: General Help
---

### Post by lucp on 2012-05-06
I just installed ubuntu near windows 7 from a usb stick. after installing I saw that grub was installed on the usb stick and not on the laptop. How can I change this??

---

### Post by oldfred on 2012-05-06
See this thread.

[http://ubuntuforums.org/showthread.php?t=1973947](http://ubuntuforums.org/showthread.php?t=1973947)

If you can boot into Ubuntu.

Check which drive is Linux.

sudo fdisk -l

if your full install in in sda once booted.

sudo grub-install /dev/sda

but if it is sdb

sudo grub-install /dev/sdb

That should overwrite the boot loader in the MBR.

But grub2 remembers where to reinstall on major grub updates.

#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

If it is not the hard drive we will need to reset that.

#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

