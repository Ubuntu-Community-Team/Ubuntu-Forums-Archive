---
title: "udev rule for specific usb bus"
date: 2010-09-12
forum: General Help
---

### Post by andrezgorapl on 2010-09-12
Hello,

I have to write a udev rule which changes permissions to certain usb buses (/dev/bus/usb/... files, libusb and openusb libraries need an acces there). Desired buses are those which have connected a mouse controller.

If I write:
```
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
```each bus has changed permissions. I don't know how to use ```
ATTRS{bInterfaceProtocol}=="02"
``` I've read in usb specification that mouse interfaces have this attribute.

Any idea?

---

