---
title: "Usb Card reader not mounting cards"
date: 2011-06-16
forum: General Help
---

### Post by jakoh on 2011-06-16
lsusb output:
Bus 005 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c50e Logitech, Inc. Cordless Mouse Receiver
Bus 003 Device 002: ID 046d:c313 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

its device 002 on Bus 005

dmesg output after inserting sd card 8gb:
[   98.960034] usb 5-1: reset full speed USB device using uhci_hcd and address 2
[  109.224044] usb 5-1: reset full speed USB device using uhci_hcd and address 2
[  125.492034] usb 5-1: reset full speed USB device using uhci_hcd and address 2
[  125.760022] usb 5-1: reset full speed USB device using uhci_hcd and address 2
[  136.024035] usb 5-1: reset full speed USB device using uhci_hcd and address 2
[  136.178940] sd 6:0:0:0: Device offlined - not ready after error recovery

this card reader device id is not listed in scsi devices supported in natty (11.04) here:
[http://www.ubuntu.com/certification/catalog/category/SCSI](http://www.ubuntu.com/certification/catalog/category/SCSI)
But other alcor micro devices are listed. 
Is there anything i can do to make this usb card reader work?

---

### Post by jakoh on 2011-06-16
Dont let your children grow up to be like me.
The problem was, after reading fragos multiple post, its an sd card reader...not an sdhc card reader. just because it fits doesnt mean it'll work. 
except if you are a mechanical engineer.

---

### Post by Neobuntu on 2011-06-22
My case, is only where the drive arrangement was different, upon Ubuntu install.

I had no USB drives (flash SDHC, camera cards, USB sticks etc.) mounting automatically. 

For me, the problem was with my SATA and PATA capable mother board. When I first installed Ubuntu 11.04, I had one temporary SATA HD internally connected, for speed. This was my critical, huge, data, that I eventually copied to my new 11.04 install, on a PATA, bigger (and faster actually) drive. My "A8V" motherboard, set the SATA as 1st, or sda1, and the PATA as 2nd, or sdb1. (Swap is inside an extended sda2, and as actual sda5; from the install.) I then removed my internal (for speed), SATA transfer drive. Thus, my one and only drive, was now fstab set (incorrectly), to /dev/sdb1 for / ! This actually booted (auto finds sda1), even though it is also somehow internally /dev/sda1; now that it's the one, and only drive, in this computer.

As root, I didn't just fix it to /dev/sda1, I looked up the blk ID, and used that in it's place. As soon as I saved the fstab, automatic USB mounting just works. I didn't even have to reboot.

```
sudo blkid -c /dev/null
```

```
sudo gedit /etc/fstab
```

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# NOTE:..was /dev/sdb1, yet booted sda1 anyway; after drive 1<SATA>, of 2<PATA>, was removed. Thus, auto mount was borked. 
UUID=####MATCH-YOUR-CORRECT-PARTITION-HERE#####   /  ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=####MATCH-YOUR-CORRECT-PARTITION-HERE##### none swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Do not use the quotes symbols from the blkid command, for your UUID, inside fstab. Just the long number; after UUID= .

My case, is only where the drive arrangement was different, upon Ubuntu install.

Hope this helps someone!

---

### Post by nick3501 on 2011-06-22
i had a similar issue with a sd/sdhc adaptor, if you leave the adaptor in the slot but remove the micro sd the computer keeps it mounted, and things get kind of funny.

---

