---
title: "Moving MBR/GRUB to USB"
date: 2010-10-04
forum: General Help
---

### Post by KRyPTyK on 2010-10-04
Hi all! I am using Ubuntu Lucid 64bit and would like to move my MBR/GRUB to a USB thumb drive. 

The basic idea is this - disable booting anything but USB in the system BIOS and have my workstation look to the USB thumb drive for the boot info. This way, the system will not boot without the thumb drive plugged in. Any help would be greatly appreciated. Thanks all!

---

### Post by oldfred on 2010-10-04
Just install grub to the USB from your install. Change sda to your USB drive.

reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda
If that returns any errors run:
sudo grub-install --recheck /dev/sda
Then:
sudo update-grub
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
spacebar to choose/unchoose drive, enter to accept, do not choose partitions


If you want to zero out your MBR you have to be careful not to zero out the partition table.
the full MBR with partitiion table is 512. So do not use any instructions that refer to 512
Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement]("https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement")
Backup the MBR e.g. 
dd if=/dev/sda of=/mbr.bin bs=446 count=1
Zero out MBR only of sda
dd if=/dev/zero of=/dev/sda bs=446 count=1

Anyone with access to your system can use another USB, livecd, floppy etc to boot so zeroing out MBR only adds slightly to difficulty booting. If really concerned you may want to encrypt folders or system, but that slows it down slightly.

---

### Post by srs5694 on 2010-10-04
> **oldfred said:**
> If you want to zero out your MBR you have to be careful not to zero out the partition table.
the full MBR with partitiion table is 512. So do not use any instructions that refer to 512
Backup MBR
[https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement](https://help.ubuntu.com/community/WindowsDualBoot#Master%20Boot%20Record%20backup%20and%20re-replacement)
Backup the MBR e.g. 
dd if=/dev/sda of=/mbr.bin bs=446 count=1
Zero out MBR only of sda
dd if=/dev/zero of=/dev/sda bs=446 count=1


Note that the MBR's code area, where the boot loader normally resides, is 440 bytes long. The next four bytes contain a disk ID number, and the next two bytes are normally 0. Thus, backing up or zeroing out 446 bytes gets all of these things. Some utilities and OSes pay attention to the disk ID number, so I wouldn't recommend zeroing out 446 bytes if you just want to wipe out the boot loader code; instead, do 440 bytes. For backup purposes, it might or might not make sense to go to 444 or 446 bytes, depending on the conditions under which you might expect to restore the data.

For further details on MBR data structures, check the [Wikipedia entry on the MBR.](http://en.wikipedia.org/wiki/Master_boot_record)

---

