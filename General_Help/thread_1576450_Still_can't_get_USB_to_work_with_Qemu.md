---
title: "Still can't get USB to work with Qemu"
date: 2010-09-17
forum: General Help
---

### Post by lumix on 2010-09-17
(10.04 x64 Desktop)

I've tried the advice that instructs one to lsusb for the manufacturer and device id, and then do something like:

```
ray@Athena:/dev/bus/usb/.usbfs$ sudo kvm -M pc -hda /vg0/DiskImages/Seven.img -m 1536 -cdrom /dev/cdrom -boot c -net nic -net user -usb -usbdevice host:04e8:681d -rtc base=localtime
```

But then I get this, and no usb device in the vm:

```
pci_add_option_rom: failed to find romfile "pxe-rtl8139.bin"
usb_create: no bus specified, using "usb.0" for "usb-host"
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
husb: open device 2.5
husb: config #1 need -1
USBDEVFS_DISCONNECT: Invalid argument
```

---

