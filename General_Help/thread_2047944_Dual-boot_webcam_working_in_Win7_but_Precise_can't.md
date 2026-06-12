---
title: "Dual-boot: webcam working in Win7 but Precise can't even see it"
date: 2012-08-25
forum: General Help
---

### Post by t0p on 2012-08-25
I bought myself a shiny new laptop the other week, a Hewlett Packard EasyNoye TS (yeah yeah, I know it isn't the best comp on the block, but finances are strained, plus it seemed to be Intel hardware which I thought was the safest bet with Ubuntu.

This laptop has a webcam.  Windows 7 knows all about - Device Manager says it's 1.3 MB HDcamera, Device type "Imaging Device",  Manufacturer Microsoft, Location 0000.001a.0000.001.003.000.000.000.0000, Details "USB Video Device".

But in Ubuntu I can't even find the camera, never mind fix it.  Windows 7 Device Manager called it a "USBdevice is Video Device", so I ran **lsusb** and got this:

```

t0p@mars:~$ lsusb         
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b21b Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 0fce:d039 Sony Ericsson Mobile Communications AB K800i (phone mode)

```

The "Sony Ericsson"  device listed is the 3G phone I often use tethered for internet access.  Chicony make various peripherals, inclusing cams, so I'm guessing 

```
Bus 001 Device 003: ID 04f2:b21b Chicony Electronics Co., Ltd
```

is the webcam.  So, how do I make it work?  It's okay in Windows;  but I was checking out the circles thing in Google, trying out the video, and she got nothing.  I checked the BIOS system, but there was nothing there about enabling/disabling anything, least of all the webcam.  And I can't see anythin under " System Settings".

So how do I get the flaming thing to work in Ubuntu?  Cheers.

---

### Post by cariboo on 2012-08-26
> Bus 001 Device 003: ID 04f2:b21b Chicony Electronics Co., Ltd

Is your web cam, and it should be well supported, try installing cheese to check if it works.

---

### Post by t0p on 2012-08-26
Thanks for the "cheese" advice, now I know for sure that the camera *does* work in Precise.

But now I gotta figure out how to activate it when I'm having conversation with someone in a Google (or is Google+?) "circles"  chat...

---

### Post by teledyn on 2013-04-05
> **t0p said:**
> Thanks for the "cheese" advice, now I know for sure that the camera *does* work in Precise.

But now I gotta figure out how to activate it when I'm having conversation with someone in a Google (or is Google+?) "circles"  chat...

You can also verify your webcams with [www.testwebcam.com](www.testwebcam.com), which will show if the Flash can access the camera, but even if it works there, it may still be ignored by Google Chat -- the google chat help page ([http://support.google.com/chat/bin/static.py?hl=en&ts=1712843&page=ts.cs](http://support.google.com/chat/bin/static.py?hl=en&ts=1712843&page=ts.cs)) claims that the "USB Video Device" means it is using a generic video driver (in Windows anyway) and that this driver lacks whatever it is that Google demands of the video feed.

so I think we're just out of luck unless someone on the kernel driver team notices the deficiency and somehow implements whatever it is in a future update of this generic driver :(

---

### Post by no2498 on 2013-04-09
make sure windows has closed all the programs for the cam in ( msconfig )
turn them off and reboot 
ubuntu only uses 1 program at a time for the cams that iv seen

---

