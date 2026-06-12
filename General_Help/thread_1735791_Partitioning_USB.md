---
title: "Partitioning USB"
date: 2011-04-21
forum: General Help
---

### Post by DrShavargo on 2011-04-21
Hey,

I'm thinking of partitioning my 16gb usb. I want 3 partitions: 1 for my various windows/ubuntu/osx files, 1 as a ubuntu backup and 1 more as a boot usb with a .iso image in it (something like system rescue CD).

I'm wondering which type of file system i should use for each partition (ext2, fat32, ntfs, linux-swap, etc.) to be compatible with windows, in the case of the first one, simple backup for the second one and my dell boot manager for the third one.

Thanks in advance!

---

### Post by DrShavargo on 2011-04-21
Hey,

I'm thinking of partitioning my 16gb usb. I want 3 partitions: 1 for my  various windows/ubuntu/osx files, 1 as a ubuntu backup and 1 more as a  boot usb with a .iso image in it (something like system rescue CD).

I'm wondering which type of file system i should use for each partition  (ext2, fat32, ntfs, linux-swap, etc.) to be compatible with windows, in  the case of the first one, simple backup for the second one and my dell  boot manager for the third one.

Thanks in advance!

---

### Post by C.S.Cameron on 2011-04-21
Windows only sees the first one so FAT32, ext2 should be ok for the second, not sure what Dell likes for the 3rd.

---

### Post by hwttdz on 2011-04-21
I'd actually put the boot partition first, as sometimes it makes life easier.  So the boot partition will be an iso, probably made by unetbootin or similar.  

For the ubuntu backup you can use ext4.  

For the mac/windows/linux, I'm thinking fat32.  There are some file size restrictions, but I'm guessing you won't hit them on a usb drive, and I believe it's quicker than ntfs.  Though ntfs would also work.

---

### Post by howefield on 2011-04-21
Duplicate threads merged.

Please keep to one thread per issue. Thanks.

---

### Post by hwttdz on 2011-04-21
And wow, is it true that windows only sees the first partition on a usb device?  That's ridiculous.  I'll happily trade 30 seconds of hassle in installing flash for being able to read usb sticks.

---

### Post by oldfred on 2011-04-21
I have 3 different USB flash drives. Two are formated with FAT32 and both boot with grub2. I have the win7 repair install and a couple of ISOs on a 2GB. I have 4 or 5 ISOs on my 4GB. And I have a full install (currently Natty) on my 16GB.

These automate the process of booting ISOs. I did it manually before I found these scripts.
This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

ISO Booting with Grub 2 - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
HOWTO: Boot & Install Ubuntu ISO from the Grub Rescue Prompt
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")

---

