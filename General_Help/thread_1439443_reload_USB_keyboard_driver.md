---
title: "reload USB keyboard driver"
date: 2010-03-26
forum: General Help
---

### Post by loki_dre on 2010-03-26
Hello,
I have a usb barcode reader that acts as a usb keyboard, but SOMETIMES when I boot up the device is not properly recognised.
I find that if I unplug and plug back in the device it always works.
Is there a way to do this in software without having to physically plug/unplug the device

I tried the following command but it did not seem to help:
modprobe -r usbhid && modprobe usbhid

---

