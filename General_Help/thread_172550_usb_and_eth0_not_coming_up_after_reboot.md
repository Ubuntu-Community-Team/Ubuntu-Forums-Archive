---
title: "usb and eth0 not coming up after reboot"
date: 2006-05-08
forum: General Help
---

### Post by russelld on 2006-05-08
Hi 
Eth0 and usb are not comming up after a reboot.](*,) 

lsusb doesn't find any devices:
dmesg gives;
```

[4294675.512000] usbcore: registered new driver usbfs
[4294675.512000] usbcore: registered new driver hub
[4294676.274000] usb 1-2: new full speed USB device using ohci_hcd and address 2
[4294676.964000] usb 1-2: new full speed USB device using ohci_hcd and address 3
[4294677.333000] usb 2-2: new low speed USB device using ohci_hcd and address 2

```

whereas liveCD dmesg has usb:

```

[4294669.794000] usbcore: registered new driver usbfs
[4294669.794000] usbcore: registered new driver hub
[4294671.140000] usb 1-2: new full speed USB device using ohci_hcd and address 3
[4294671.429000] usb 2-2: new low speed USB device using ohci_hcd and address 2
[4294672.072000] usbcore: registered new driver hiddev
[4294672.118000] input: USB HID v1.10 Mouse [Microsoft Basic Optical Mouse] on usb-0000:00:03.1-2
[4294672.118000] usbcore: registered new driver usbhid
[4294672.118000] drivers/usb/input/hid-core.c: v2.01:USB HID core driver
[4294672.917000] usbcore: registered new driver usbkbd
[4294672.917000] drivers/usb/input/usbkbd.c: :USB HID Boot Protocol keyboard driver
[4294672.931000] usbcore: registered new driver usbserial
[4294672.935000] drivers/usb/serial/usb-serial.c: USB Serial support registered for Generic
[4294672.939000] usbcore: registered new driver usbserial_generic
[4294672.939000] drivers/usb/serial/usb-serial.c: USB Serial Driver core v2.0
[4294715.092000] usbcore: registered new driver usb-storage
[4294997.501000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04A9 pid 0x1056
[4294997.506000] usbcore: registered new driver usblp
[4294997.506000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver

```

network has to be manually restored via:
ifconfig lo up
ifconfig eth0 up
dhclient3

dmesg section for eth0
```
[4294684.369000] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 169, 00:c0:9f:b1:4c:0a.
```

and liveCD dmesg:
```

[4294707.898000] eth0: SiS 900 PCI Fast Ethernet at 0x1800, IRQ 19, 00:c0:9f:b1:4c:0a.
[4294715.892000] eth0: Media Link On 100mbps full-duplex
[4294999.568000] eth0: no IPv6 routers present

```

what's going on here?

how can this be fixed?

All help appreciated

TIA

Russell

---

### Post by russelld on 2006-05-10
eth0 is coming up and configured correctly

usb is still not been seen by lsusb and only runs as root user, even after setting permissions to 755

---

