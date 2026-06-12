---
title: "USB mass storage devices, Mount problem"
date: 2009-11-22
forum: General Help
---

### Post by woodsmen on 2009-11-22
OS environment
 I installed "Ubuntu 9.10" on Vmware Workstation 5.0

I confirmed my usb device(vmware --> VM --> removable devices --> USB devices )
and then checked kernel messages and "lsusb" message.

kernel messages
dmesg | tail -n 20

-------------------------------------------------------------------------
[  241.926553] scsi3 : SCSI emulation for USB Mass Storage devices
[B][COLOR="Blue"][  241.927493] usbcore: registered new interface driver usb-storage
[  241.927524] USB Mass Storage support registered.
[  241.928653] usb-storage: device found at 2
[  241.928680] usb-storage: waiting for device to settle before scanning
[  246.939983] usb-storage: device scan complete[/COLOR][/B]
[  247.060521] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[  247.841145] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[  248.910174] usb 1-1: reset full speed USB device using uhci_hcd and address 2
[  249.597615] usb 1-1: reset full speed USB device using uhci_hcd and address 2
-----------------------------------------------------------------------
$ lsusb 
[COLOR="Blue"]Bus 001 Device 002: ID 090c:1000 Feiya Technology Corp. Flash Drive[/COLOR] --> [COLOR="Red"]it's my usb device(memory stick[/COLOR])
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

$ sudo fdisk -l
....
[COLOR="Red"]not found my usb storage's infomation.
so i couldn't manually mount usb device.
And usb was not mounted automatically.[/COLOR]
-----------------------------------------
I guess my problems. below..
1. vmware workstation version is old.

2. will be setting more on ubuntu & vmware
  - about auto mount.

--------------------------------------------

** additional info.
I modified /etc/fstab
add line
--> usbfs /proc/bus/usb usbfs auto 0 0

what's wrong with me?

---

### Post by dcstar on 2009-11-23
> **woodsmen said:**
> OS environment
 I installed "Ubuntu 9.10" on Vmware Workstation 5.0
.........
what's wrong with me?

There are numerous posts on this in the Virtualization forum.

---

### Post by woodsmen on 2009-11-23
Ok. I'll check the Virtualization forum.
Thanks.

---

