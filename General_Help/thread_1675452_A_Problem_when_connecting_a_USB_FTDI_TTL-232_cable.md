---
title: "A Problem when connecting a USB FTDI TTL-232 cable"
date: 2011-01-25
forum: General Help
---

### Post by Atrus6 on 2011-01-25
I am trying to connect this cable

[http://www.adafruit.com/index.php?main_page=product_info&cPath=33&products_id=70](http://www.adafruit.com/index.php?main_page=product_info&cPath=33&products_id=70)

however, it refuses to connect properly. It previously connected, but now whenever I plug it in, nothing happens.

lsusb before:
```
atrus@Fiona:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 011: ID 046d:c041 Logitech, Inc. G5 Laser Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

lsusb after:

```
atrus@Fiona:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 011: ID 046d:c041 Logitech, Inc. G5 Laser Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

dmesg error:

```
[ 2194.004437] usb 3-1: new full speed USB device using uhci_hcd and address 26
[ 2194.124024] usb 3-1: device descriptor read/64, error -71
[ 2194.348028] usb 3-1: device descriptor read/64, error -71
[ 2194.564026] usb 3-1: new low speed USB device using uhci_hcd and address 27
[ 2194.796039] usb 3-1: new low speed USB device using uhci_hcd and address 28
[ 2195.204021] usb 3-1: device not accepting address 28, error -71
[ 2195.316029] usb 3-1: new full speed USB device using uhci_hcd and address 29
[ 2195.724031] usb 3-1: device not accepting address 29, error -71
[ 2195.724059] hub 3-0:1.0: unable to enumerate USB device on port 1
```

From some other googling, is seemed as if removing "ehci_hcd" or "uhci_hcd" would fix it, however running the following commands does nothing, as shown below:


```
atrus@Fiona:~$ sudo rmmod ehci_hcd
ERROR: Module ehci_hcd does not exist in /proc/modules
atrus@Fiona:~$ sudo rmmod uhci_hcd
ERROR: Module uhci_hcd does not exist in /proc/modules
```


So, I'm at a loss, what are your suggestions?

---

### Post by Atrus6 on 2011-01-25
I also tried setting:

```
/sys/module/usbcore/parameters/old_scheme_first
```

to Y

and

```
/sys/module/usbcore/parameters/autosuspend
```

to -1

Still at a loss!

---

