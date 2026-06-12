---
title: "ls: cannot access /dev/video: No such file or directory"
date: 2011-01-31
forum: General Help
---

### Post by Zizo on 2011-01-31
Hi,

I am trying to run an old Webcam on Ubuntu 10.04.

Before and after plugging it onto the USB, no /dev/video block device is created.
Shouldn't /dev/video be created even without any plugged in cam?
I would also like to know if that means my Webcam is not supported or I have a problem in my ubuntu installation that is making /dev/video not there.

I have seen many users with the same problem, but it was never firmly solved or explained.

my kernel version is: 2.6.32-28-generic-pae

lsusb: (camera plugged in)
```

Bus 005 Device 002: ID 0458:7001 KYE Systems Corp. (Mouse Systems) 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```dmesg | tail -n 3

```

[ 1468.080067] usb 2-2: USB disconnect, address 2
[ 1482.556019] usb 5-1: new full speed USB device using uhci_hcd and address 2
[ 1482.807187] usb 5-1: configuration #1 chosen from 1 choice

```any help is appreciated, thanks

---

