---
title: "WD MyBook (USB3.0) not working with USB3.0 card"
date: 2011-01-05
forum: General Help
---

### Post by anescient on 2011-01-05
Ubuntu 10.10, 32 bit

I've got a 2TB WD external disk which has USB 3.0, and I have a USB 3.0 PCIe card.

lspci for the card: ```
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 03)
```

Plugging the drive into the card has no effect at all. The drive powers itself up, but the kernel log is silent. A USB 2.0 flash disk works properly with the card, and the WD disk works properly plugged into a USB 2.0 port, but the combination of the 3.0 disk and the 3.0 card is completely nonfunctional, even when using a small extension cable to cut off the superspeed connection.

I found this in the kernel log: ```
usb usb8: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values
```

Searching suggested that this is because of a bug which would prevent superspeed from working, but should -not- cause complete failure (highspeed fallback should be OK). I tried the suggested fix for this anyway, which was to install kernel 2.6.37-020637rc1 (was 2.6.35-24-generic). This did not help my problem nor did it correct that endpoint error message.

I don't know what to try next.

---

### Post by anescient on 2011-01-05
I have just booted Natty alpha 1 to see how things look. Kernel is 2.6.37-7-generic

The same "No SuperSpeed endpoint" error appears in the log.

The disk still does not work with the 3.0 card, but there is some response to plugging it in:
```
[  220.200068] usb 8-4: new high speed USB device using xhci_hcd and address 2
[  220.752390] xhci_hcd 0000:04:00.0: WARN: transfer error on endpoint
[  220.752888] xhci_hcd 0000:04:00.0: WARN: transfer error on endpoint
[  220.753389] xhci_hcd 0000:04:00.0: WARN: transfer error on endpoint
[  220.753402] usb 8-4: device descriptor read/8, error -71
[  220.872388] xhci_hcd 0000:04:00.0: WARN: transfer error on endpoint
[  220.872887] xhci_hcd 0000:04:00.0: WARN: transfer error on endpoint
[  220.873387] xhci_hcd 0000:04:00.0: WARN: transfer error on endpoint
[  220.873399] usb 8-4: device descriptor read/8, error -71
[  221.032039] hub 8-0:1.0: unable to enumerate USB device on port 4

```
Again, the disk does not work at all, even at a reduced speed. But these messages are more than I can get out of 10.10.

---

### Post by anescient on 2011-01-06
I may have a hardware problem here. I tried Windows XP and I got the same broken behavior. I will return the card and try another brand.

I'm pretty sure the chip on this card is about the only chip out there, so I would still appreciate some information about those endpoint errors.

---

### Post by insaini on 2011-03-09
I have the exact same chipset in a vantec card.

[    9.933516] usb usb9: No SuperSpeed endpoint companion for config 1  interface 0 altsetting 0 ep 129: using minimum values

Disk Utility clearly says connection is 480.0 MB/s

---

