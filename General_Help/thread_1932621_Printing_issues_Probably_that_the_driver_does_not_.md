---
title: "Printing issues: Probably that the driver does not load"
date: 2012-02-27
forum: General Help
---

### Post by desm on 2012-02-27
Hi There,

I've been trying to get my Epson Stylus SX420W to scan to my laptop. It has done this successfully before, and I believe I have all the relevant drivers installed. Yet it has stopped being able to scan to the laptop except using VueScan, which is proprietary and watermarks images.

The output of sane-find-scanner is:

```
found USB scanner (vendor=0x04b8, product=0x0864) at libusb:002:002

```

Yet scanimage -L and xsane report that there is no scanner in place. 

The printer still works however. This leads me to suspect that the issue is that the printer drivers do not load automatically, as VueScan promises to be able to print out of the box, I guess due to separate drivers.

Is this likely to be my problem? If so, or if not, how would I go about fixing this issue permanently?

Thankyou in advance!

Desm

---

