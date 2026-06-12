---
title: "Problem with USB devices"
date: 2012-08-06
forum: General Help
---

### Post by JCM_Pico on 2012-08-06
Hi there,

When I connect my mouse to an USB port I get this error message in my dmesg... Nonetheless my mouse don't work properly 

```
[   90.039523] usb 3-1: new low-speed USB device number 3 using xhci_hcd
[   90.114819] usb 3-1: New USB device found, idVendor=04f3, idProduct=00a4
[   90.114827] usb 3-1: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[   90.114832] usb 3-1: Product: 2.4G RX
[   90.115068] ACPI Exception: AE_AML_PACKAGE_LIMIT, Index (0x0000000000000008) is beyond end of object (20120320/exoparg2-418)
[   90.115083] ACPI Error: Method parse/execution failed [\_SB_.PCI0.XHC_.RHUB.HSP1._PLD] (Node ffff880119145078), AE_AML_PACKAGE_LIMIT (20120320/psparse-536)
[   90.115490] usb 3-1: ep 0x81 - rounding interval to 64 microframes, ep desc says 80 microframes
[   90.203415] input: 2.4G RX as /devices/pci0000:00/0000:00:14.0/usb3/3-1/3-1:1.0/input/input11
[   90.203769] hid-generic 0003:04F3:00A4.0002: input,hidraw0: USB HID v1.10 Keyboard [2.4G RX] on usb-0000:00:14.0-1/input0
[   92.762526] xhci_hcd 0000:00:14.0: WARN Event TRB for slot 2 ep 0 with no TDs queued?

```

Any help or advice ?

---

