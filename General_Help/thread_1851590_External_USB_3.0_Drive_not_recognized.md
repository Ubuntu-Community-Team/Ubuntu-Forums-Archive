---
title: "External USB 3.0 Drive not recognized"
date: 2011-09-28
forum: General Help
---

### Post by jjman75 on 2011-09-28
I have two systems currently running fully updated version 10.10 Ubuntu.  They are both fairly new high end work stations.  I need to be able to access large quantities on data from external drives.  The external drives I selected are 2Tb WD MyBook 3.0 drives.  All of my windows computers recognize them just fine.  I have installed a  NEC USB 3.0 pci card installed with a mukn usb 3.0 hub connected to it.  Ubuntu doesn't even detect the drives.  I am fairly new to Linux and Ubuntu so any help would be greatly appreciated.

relevant dmesg response:
```

[  182.020481] usb 9-4.4: new high speed USB device using xhci_hcd and address 0
[  182.247856] usb 9-4.4: Device not responding to set address.
[  182.450485] usb 9-4.4: Device not responding to set address.
[  182.660088] usb 9-4.4: device not accepting address 0, error -71
[  182.680990] hub 9-4:1.0: unable to enumerate USB device on port 4

```

lsusb response:
```

Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 046b:ff10 American Megatrends, Inc. 
Bus 002 Device 004: ID 046b:ff01 American Megatrends, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

relevant lspci response:
```

81:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)

```

---

