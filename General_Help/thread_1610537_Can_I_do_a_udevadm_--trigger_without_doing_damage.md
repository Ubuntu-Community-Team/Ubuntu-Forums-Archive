---
title: "Can I do a udevadm --trigger without doing damage?"
date: 2010-10-31
forum: General Help
---

### Post by strider22 on 2010-10-31
I have an MP3 player MP600 that is seen by udevadm as below but it does not get linked into places/removable media.

lsusb shows the device on bus 5... the same one the internal camera is on. This puzzles me because everything else plugged into the usb ports is on bus 1,2 or 3. Both ports on the right side are bus 1. the ports on the right are bus 2 and 3.
Bus 005 Device 015: ID 1e74:6823 
Note no ID/name is given

How do I get access to the device?

Can I do a udevadm --trigger without doing damage?
I'm hoping that might make it create the /dev link.

#udevadm info --export-db  (just the relevant part)

P: /block/sde
N: sde
S: disk/by-id/usb-MP600_HS_USB_FlashDisk_4512482ADF0FE
S: disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0
E: DEVTYPE=disk
E: ID_VENDOR=MP600
E: ID_MODEL=HS_USB_FlashDisk
E: ID_REVISION=0100
E: ID_SERIAL=MP600_HS_USB_FlashDisk_4512482ADF0FE
E: ID_SERIAL_SHORT=4512482ADF0FE
E: ID_TYPE=floppy
E: ID_BUS=usb
E: ID_PATH=pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0

Does the ID_TYPE=floppy provide a hint to the method to use?

---

### Post by strider22 on 2010-10-31
The /sde is only in 2 of the 4 expected lists in /dev/disk.

 ls -l /dev/disk/by-id/
lrwxrwxrwx 1 root root  9 2010-10-31 16:57 usb-MP600_HS_USB_FlashDisk_4512482ADF0FE -> ../../sde
 ls -l /dev/disk/by-path/
lrwxrwxrwx 1 root root  9 2010-10-31 16:57 pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0 -> ../../sde

but it is not in
 ls -l /dev/disk/by-label/  or
 ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 2010-10-30 16:27 18F1-3418 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2010-10-30 16:10 6E32565E32562AFB -> ../../sdc1
lrwxrwxrwx 1 root root 10 2010-10-30 11:25 74AE1A37AE19F1FA -> ../../sda2
lrwxrwxrwx 1 root root 10 2010-10-30 11:25 76840F0D840ECF93 -> ../../sda3
lrwxrwxrwx 1 root root 10 2010-10-30 15:40 A1C6-704B -> ../../sdd1
lrwxrwxrwx 1 root root 10 2010-10-30 16:27 A2C0C674C0C64DEB -> ../../sdb5
lrwxrwxrwx 1 root root 10 2010-10-30 11:25 ad2076e1-8d0e-45bb-b821-e16fe9846036 -> ../../sda4
lrwxrwxrwx 1 root root 10 2010-10-30 11:25 D0041350041338C4 -> ../../sda1


I also note that the usb hard drives have extra lines in udevadm regarding file system.
E: ID_FS_USAGE=filesystem
E: ID_FS_TYPE=vfat
E: ID_FS_VERSION=FAT32

Can I make any tests to figure out the filesystem for this device that will be non-destructive.

---

### Post by strider22 on 2010-10-31
When a usb stick is inserted, it gets linked in with sde1, a UUID and in sde1 the filesystem info is presented.

#udevadm info --export-db (just the relevant part)
P: /block/sde
N: sde
S: disk/by-id/usb-0930_USB_Flash_Memory_09814A402213AA31-0:0
S: disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0
E: DEVTYPE=disk
E: ID_VENDOR=0930
E: ID_MODEL=USB_Flash_Memory
E: ID_REVISION=1.00
E: ID_SERIAL=0930_USB_Flash_Memory_09814A402213AA31-0:0
E: ID_SERIAL_SHORT=09814A402213AA31
E: ID_TYPE=disk
E: ID_INSTANCE=0:0
E: ID_BUS=usb
E: ID_PATH=pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0

P: /block/sde/sde1
N: sde1
S: disk/by-id/usb-0930_USB_Flash_Memory_09814A402213AA31-0:0-part1
S: disk/by-path/pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0-part1
S: disk/by-uuid/D031-2827
E: DEVTYPE=partition
E: ID_VENDOR=0930
E: ID_MODEL=USB_Flash_Memory
E: ID_REVISION=1.00
E: ID_SERIAL=0930_USB_Flash_Memory_09814A402213AA31-0:0
E: ID_SERIAL_SHORT=09814A402213AA31
E: ID_TYPE=disk
E: ID_INSTANCE=0:0
E: ID_BUS=usb
E: ID_PATH=pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0
E: ID_FS_USAGE=filesystem
E: ID_FS_TYPE=vfat
E: ID_FS_VERSION=FAT16
E: ID_FS_UUID=D031-2827
E: ID_FS_UUID_ENC=D031-2827
E: ID_FS_LABEL=
E: ID_FS_LABEL_ENC=
E: ID_FS_LABEL_SAFE=

Using the ID_PATH and the by-path list we can confirm the /dev/sde creation
ls -l /dev/disk/by-path/
lrwxrwxrwx 1 root root  9 2010-10-31 22:45 pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0 -> ../../sde
lrwxrwxrwx 1 root root 10 2010-10-31 22:45 pci-0000:00:1d.7-usb-0:5:1.0-scsi-0:0:0:0-part1 -> ../../sde1

and this is mounted on /media/disk-1/ (although I can't prove it yet - prob because my o/s is too old and doesn't support udisks )

---

### Post by strider22 on 2010-11-18
continuing as a question on writing udev rules at 
[http://ubuntuforums.org/showthread.php?p=10132530#post10132530](http://ubuntuforums.org/showthread.php?p=10132530#post10132530)

---

