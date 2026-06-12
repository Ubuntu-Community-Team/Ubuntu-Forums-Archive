---
title: "USB 3 drive half recognised"
date: 2012-07-17
forum: General Help
---

### Post by adamski99 on 2012-07-17
Hi,

I have a USB 3 external drive that seems to be recognized but not assigned a /dev/sdb or mounted.

Sometimes if i boot with the drive plugged in it will mount fine but most of the time not.

Also it is always recognized by VMWare and can be assigned to a host vm, then when deassigned it is recognized and mounts automatically.

this is what appears in the syslog on plugin:

```

Jul 17 23:17:04 adam-MacBookPro kernel: [ 2074.916850] usb 4-1: new SuperSpeed USB device number 8 using xhci_hcd
Jul 17 23:17:04 adam-MacBookPro kernel: [ 2074.933972] scsi12 : usb-storage 4-1:1.0
Jul 17 23:17:04 adam-MacBookPro mtp-probe: checking bus 4, device 8: "/sys/devices/pci0000:00/0000:00:14.0/usb4/4-1"
Jul 17 23:17:04 adam-MacBookPro mtp-probe: bus: 4, device: 8 was not an MTP device

```

and with  udevadm monitor:

```

adam@adam-MacBookPro:/sys/block$ udevadm monitor
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent

KERNEL[2354.966289] add      /devices/pci0000:00/0000:00:14.0/usb4/4-1 (usb)
KERNEL[2354.967253] add      /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1:1.0 (usb)
KERNEL[2354.967814] add      /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1:1.0/host14 (scsi)
KERNEL[2354.967847] add      /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1:1.0/host14/scsi_host/host14 (scsi_host)
UDEV  [2354.973360] add      /devices/pci0000:00/0000:00:14.0/usb4/4-1 (usb)
UDEV  [2354.976608] add      /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1:1.0 (usb)
UDEV  [2354.976655] add      /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1:1.0/host14 (scsi)
UDEV  [2354.976688] add      /devices/pci0000:00/0000:00:14.0/usb4/4-1/4-1:1.0/host14/scsi_host/host14 (scsi_host)


```
its listed in lsusb (Genesys Logic, Inc. ):

```

adam@adam-MacBookPro:/sys/block$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 045e:00d2 Microsoft Corp. 
Bus 004 Device 009: ID 05e3:0731 Genesys Logic, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 05ac:8509 Apple, Inc. FaceTime HD Camera
Bus 002 Device 003: ID 0424:2513 Standard Microsystems Corp. 
Bus 002 Device 007: ID 05ac:820a Apple, Inc. 
Bus 002 Device 008: ID 05ac:820b Apple, Inc. 
Bus 002 Device 009: ID 05ac:821d Apple, Inc. 
Bus 002 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 002 Device 005: ID 05ac:8242 Apple, Inc. IR Receiver [built-in]
Bus 002 Device 006: ID 05ac:0253 Apple, Inc. Internal Keyboard/Trackpad (ISO)

```

btw im running 12.04 with 3.5.0-4 kernel,

Any ideas?

Cheers

Ads :)

---

### Post by adamski99 on 2012-08-16
ok, 

could anyone tell me what module might handle this part of the process?

or any other ideas?

cheers

ads

---

