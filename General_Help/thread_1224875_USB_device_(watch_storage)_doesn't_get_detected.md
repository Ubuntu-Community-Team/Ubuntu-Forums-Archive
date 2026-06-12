---
title: "USB device (watch storage) doesn't get detected"
date: 2009-07-27
forum: General Help
---

### Post by Replicon on 2009-07-27
Hey all,

I'm running 8.04, and am encountering an annoyance with a new USB device not being detected.

Usually, USB drives and the likes work perfectly with this laptop. With this one, however (a watch with a camera), when I plug it in, it just goes into "battery charge" mode. When I tail /var/log/messages, nothing pops up as I plug it in.

FWIW:

```

lsmod | grep usb
usbhid                 35680  0 
hid                    44992  1 usbhid
usbcore               170288  5 uvcvideo,usbhid,ehci_hcd,uhci_hcd

```

How should I proceed?

thanks!

---

