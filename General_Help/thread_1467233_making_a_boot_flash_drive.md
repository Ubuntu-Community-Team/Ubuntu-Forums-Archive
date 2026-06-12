---
title: "making a boot flash drive"
date: 2010-04-30
forum: General Help
---

### Post by buckley310 on 2010-04-30
i am trying to make a windows XP boot flash drive for one of my  copmputers. i delete all the partitions on my flash drive and run "dd  if=/dev/cdrom of=/dev/sdb" and ubuntu can read it and its got all the  contents of the CD but windows machines say i need to format it and no  computer can boot off of it. did i do something wrong?

---

### Post by quadproc on 2010-04-30
> **buckley310 said:**
> i am trying to make a windows XP boot flash drive for one of my  copmputers. i delete all the partitions on my flash drive and run "dd  if=/dev/cdrom of=/dev/sdb" and ubuntu can read it and its got all the  contents of the CD but windows machines say i need to format it and no  computer can boot off of it. did i do something wrong?
What kind of file system is on the flash drive?  ext3, reiserfs, ntfs, FAT16, FAT32, etc.
I don't know what XP will require in terms of a boot so you may need to install that separately, and you may also need to set one or flags in the boot sector.

quadproc

---

### Post by buckley310 on 2010-04-30
that flash drive is unallocated. since ubuntu can read it i sort of figured it also coppied whatever format it needs

---

### Post by quadproc on 2010-04-30
> **buckley310 said:**
> that flash drive is unallocated. since ubuntu can read it i sort of figured it also coppied whatever format it needs
You should be able to learn something about the flash drive by using the Ubuntu tools such as gparted.  Try running gparted with the flash drive plugged in and select it in the device portion of gparted's window (upper right).  If there are any recognizable filesystems on the drive they should show up as entries in addition to the unallocated.

quadproc

---

### Post by buckley310 on 2010-04-30
there are no filesystems on it but ubuntu can still read the files off of it... weird. should i try making a fat32 partition before using dd?

---

### Post by oldfred on 2010-04-30
I saved these links but have not try any of these:

Copy Windows XP to usb
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)
Please note this tutorial works on all computers not just the Asus EEE PC.
[http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html](http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html)
USB install of XP
[http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html](http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html)
[http://www.ngine.de/article/id/8](http://www.ngine.de/article/id/8)
non-commercial all versions of windows
[http://wintoflash.com/home/en/](http://wintoflash.com/home/en/)

---

