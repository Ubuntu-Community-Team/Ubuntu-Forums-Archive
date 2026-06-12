---
title: "F-spot/gthumb - &quot;could not lock the device&quot;"
date: 2010-05-22
forum: General Help
---

### Post by Baryon on 2010-05-22
Importing photos from my Fuji FinePix S1730 using F-Spot on Ubuntu 9.04 used to work fine, but today I got the error "could not lock the device". Usually a dialog box comes up as soon as I plug the camera in, but today it didn't. I noticed the following message in dmesg:

```
[ 2781.148175] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd gthumb rqt 128 rq 6 len 1000 ret -110
```

That's when I tried it with gthumb, which gives the same problem. Sometimes the camera isn't detected at all, incidentally. I tried reinstalling f-spot to no avail.

Other people with this problem said that they needed to unmount the camera first, but my camera isn't mounted in the first place and it doesn't appear in Nautilus. Any ideas? Thanks.

---

### Post by no2498 on 2010-05-22
have you tried to restart the computer with the cam plugged in and not plugged in

sounds like you had a bad unmount

---

### Post by Baryon on 2010-05-23
I restarted with the camera plugged in, and I had the following messages during start-up:
> usb 1-3: device descriptor read/64, error -110
usb 1-3: device not accepting address 4, error -110
usb 1-3: device not accepting address 5, error -110
hub 1-0:1.0: unable to enumerate USB device on port 3


---

