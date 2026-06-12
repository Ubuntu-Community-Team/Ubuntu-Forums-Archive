---
title: "Opening a cash drawer via /dev/"
date: 2011-09-17
forum: General Help
---

### Post by zackloki on 2011-09-17
I purchased a USB interface cash drawer to use with Ubuntu 10.04, though the manual only has instructions for windows use.

I've spent several hours trying to determine how to send it the open signal. I've tried several commands on pretty much everything in the /dev/ directory that has usb in it's name including:
cat /dev/usb/hiddev0 | hexdump
and
echo 1 > /dev/usb/hiddev0

Using the cat command I was able to read a signal every time I opened it, but that's about it.

dmesg output:
```
[203123.286726] usb 2-1.2: new low speed USB device using ehci_hcd and address 14
[203123.405248] generic-usb 0003:06E5:0008.000B: hiddev0,hidraw2: USB HID v1.00 Device [M-S Cash Drawer M-S Cash Drawer USB Device] on usb-0000:00:1d.0-1.2/input0
```

lsusb entry:
```
Bus 002 Device 018: ID 06e5:0008
```
(description column is blank)

Thanks

---

