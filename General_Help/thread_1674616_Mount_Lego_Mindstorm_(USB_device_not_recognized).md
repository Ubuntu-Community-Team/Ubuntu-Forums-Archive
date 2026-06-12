---
title: "Mount Lego Mindstorm (USB device not recognized)"
date: 2011-01-24
forum: General Help
---

### Post by antuneleta on 2011-01-24
Hi everybody,
I searched a lot in the community before writing but I didn't find my case.

I'm working with the Lego Mindstorm NXT device. Actually, I'm writing some behavior with Java LeJos and I need to connect my brick to upload my code.

When I connect the brick (USB) I don't have feedback from my computer. The computer doesn't mount the device.

This the output of dmesg:
```
[ 3487.972028] usb 4-2: new full speed USB device using uhci_hcd and address 3
[ 3488.148154] usb 4-2: configuration #1 chosen from 1 choice
[ 3847.640054] usb 4-2: USB disconnect, address 3

```This the output of fdisk -l:
```
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00063c94

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9356    75146240   83  Linux
/dev/sda2            9356        9726     2975745    5  Extended
/dev/sda5            9356        9726     2975744   82  Linux swap / Solaris

```This the output of blkid:
```
/dev/sda1: UUID="311159b6-36e8-46c5-ac74-fc2b8aafc39d" TYPE="ext4" 
/dev/sda5: UUID="af1cc82f-3165-4d01-ac35-81dca2c9bcac" TYPE="swap"
```And this the output of lsusb:
```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 0694:0002 Lego Group 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 003 Device 002: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```I don't know what to do.
I just can see the device in the list of usb connected but nothing more. It seems that the system doesn't recognize the device. I'm becoming crazy!!!!
Someone can help me? :)

---

### Post by silpol on 2011-08-18
Hope you've got enough time to find answer ;)
there is at least one place where you could find answer - [Using Lego Mindstorms NXT with Ubuntu Linux]("http://ubuntudaily.blogspot.com/2011/03/using-lego-mindstorms-nxt-with-ubuntu.html")

---

