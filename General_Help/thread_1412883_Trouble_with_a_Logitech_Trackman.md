---
title: "Trouble with a Logitech Trackman"
date: 2010-02-21
forum: General Help
---

### Post by DiscoStu570 on 2010-02-21
Specifically, this device here:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16826104249&cm_re=logitech_trackman-_-26-104-249-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16826104249&cm_re=logitech_trackman-_-26-104-249-_-Product)

I've had this for a bit now, mostly using it with my laptop, which runs Windows XP.  It continues to work just fine on that machine.  However, on my desktop (running Ubuntu 9.10), it fails.  Sometimes, when I plug it in, it will work for about ten or fifteen seconds, and then stop, but most of the time it simply isn't detected.

lsusb returns no trace of it, and neither does cat /proc/bus/input/devices.

I don't believe it's a hardware issue, as every other USB device I plug in, including a different usb optical mouse, works just fine.

Any thoughts?

Edit:  If this belongs in a different forum please say so, I suspect that it may, but General Help seemed a fine place to start.

---

### Post by DiscoStu570 on 2010-02-21
The output from sudo dmesg | tail -n 20

[12335.576039] usb 4-1: new low speed USB device using uhci_hcd and address 118
[12335.696025] usb 4-1: device descriptor read/64, error -71
[12335.920058] usb 4-1: device descriptor read/64, error -71
[12336.136037] usb 4-1: new low speed USB device using uhci_hcd and address 119
[12336.544024] usb 4-1: device not accepting address 119, error -71
[12336.656032] usb 4-1: new low speed USB device using uhci_hcd and address 120
[12337.072026] usb 4-1: device not accepting address 120, error -71
[12337.072055] hub 4-0:1.0: unable to enumerate USB device on port 1
[12365.008045] usb 4-1: new low speed USB device using uhci_hcd and address 121
[12365.128023] usb 4-1: device descriptor read/64, error -71
[12365.356094] usb 4-1: device descriptor read/64, error -71
[12365.572540] usb 4-1: new low speed USB device using uhci_hcd and address 122
[12365.696927] usb 4-1: device descriptor read/64, error -71
[12365.924027] usb 4-1: device descriptor read/64, error -71
[12366.140034] usb 4-1: new low speed USB device using uhci_hcd and address 123
[12366.548015] usb 4-1: device not accepting address 123, error -71
[12366.660039] usb 4-1: new low speed USB device using uhci_hcd and address 124
[12367.068075] usb 4-1: device not accepting address 124, error -71
[12367.068099] hub 4-0:1.0: unable to enumerate USB device on port 1
[12395.016541] usb 4-1: new low speed USB device using uhci_hcd and address 125

---

### Post by DiscoStu570 on 2010-02-22
shameless bump.

Anybody got anything to offer?

---

### Post by Swagman on 2010-02-22
I b0rked my Logitech Trackball (thumb-ball) when I cleaned the optic.

Now after every cold boot I have to unplug it and replug it before it works.

:-(

---

### Post by DukeBoxer on 2010-02-22
I fixed my logitech webcam by typing gstreamer-properties in the Terminal and making sure that the usb camera is selected in the video tab

---

