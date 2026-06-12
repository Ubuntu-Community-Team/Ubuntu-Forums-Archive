---
title: "usb flash drive/mouse malfunction no register"
date: 2011-07-20
forum: General Help
---

### Post by invalid penguin on 2011-07-20
I have a tested and working (on windows system) usb flash drive and usb mouse that do not work or even register on the three USB ports on my ubuntu OS laptop.

I get the following output for sudo fdisk -l and dmesg | tail and sudo mount /dev/sdb1 /mnt:

stephen@stephen-laptop:~$ sudo fdisk -l
[sudo] password for stephen: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5ea4f703

Device Boot Start End Blocks Id System
/dev/sda1 * 1 13995 112414806 83 Linux
/dev/sda2 13996 14593 4803435 5 Extended
/dev/sda5 13996 14593 4803403+ 82 Linux swap / Solaris
stephen@stephen-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5ea4f703

Device Boot Start End Blocks Id System
/dev/sda1 * 1 13995 112414806 83 Linux
/dev/sda2 13996 14593 4803435 5 Extended
/dev/sda5 13996 14593 4803403+ 82 Linux swap / Solaris
stephen@stephen-laptop:~$ dmesg | tail
[ 7310.082085] ehci_hcd 0000:00:13.2: port 7 reset error -110
[ 7310.082262] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 7310.286076] ehci_hcd 0000:00:13.2: port 7 reset error -110
[ 7310.286225] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 7310.490078] ehci_hcd 0000:00:13.2: port 7 reset error -110
[ 7310.490221] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 7310.694077] ehci_hcd 0000:00:13.2: port 7 reset error -110
[ 7310.694217] hub 1-0:1.0: hub_port_status failed (err = -32)
[ 7310.694220] hub 1-0:1.0: Cannot enable port 7. Maybe the USB cable is bad?
[ 7310.694233] hub 1-0:1.0: unable to enumerate USB device on port 7
stephen@stephen-laptop:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5ea4f703

Device Boot Start End Blocks Id System
/dev/sda1 * 1 13995 112414806 83 Linux
/dev/sda2 13996 14593 4803435 5 Extended
/dev/sda5 13996 14593 4803403+ 82 Linux swap / Solaris
stephen@stephen-laptop:~$ dmesg | tail
[ 7548.308058] usb 2-3: device descriptor read/64, error -62
[ 7548.592029] usb 2-3: device descriptor read/64, error -62
[ 7548.872035] usb 2-3: new full speed USB device using ohci_hcd and address 23
[ 7549.052028] usb 2-3: device descriptor read/64, error -62
[ 7549.336117] usb 2-3: device descriptor read/64, error -62
[ 7549.616023] usb 2-3: new full speed USB device using ohci_hcd and address 24
[ 7550.024023] usb 2-3: device not accepting address 24, error -62
[ 7550.200023] usb 2-3: new full speed USB device using ohci_hcd and address 25
[ 7550.608022] usb 2-3: device not accepting address 25, error -62
[ 7550.608069] hub 2-0:1.0: unable to enumerate USB device on port 3
stephen@stephen-laptop:~$ ^C
stephen@stephen-laptop:~$ sudo mount /dev/sdb1 /mnt
mount: special device /dev/sdb1 does not exist
stephen@stephen-laptop:~$ 

Any help would be appreciated.

---

