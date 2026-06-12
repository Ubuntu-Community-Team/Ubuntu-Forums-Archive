---
title: "/dev/video0 dissapears when using motion deamon"
date: 2011-01-29
forum: General Help
---

### Post by epud on 2011-01-29
Hi

I am trying to get my system up and running with motion (motion detection software).

After a reboot I have the video device */dev/video0*

But then when I start the daemon

```
sudo /etc/init.d/motion start
```

is says [ OK ]

but now the devide */dev/video0* is no longer there and motion won't start up.

```
Failed to open video device /dev/video0: No such file or directory
```

The only way to get the video0 device back is rebooting. 

**Anybody know what the problem is?**

---

### Post by no2498 on 2011-01-29
does the cam work in other programs like cheese

? you sure you need to run motion as sudo

---

### Post by epud on 2011-01-29
> **no2498 said:**
> does the cam work in other programs like cheese

? you sure you need to run motion as sudo

Hi! Actually it does not work in Cheese or Skype. (just did a reboot). The light on the webcam is on and it seems it is detected to some degree. 

```
lsusb

Bus 004 Device 006: ID 0471:0329 Philips (or NXP) SPC 900NC PC Camera / ORITE CCD Webcam(PC370R)
```

I am doing a sudo because if I don't I get:

```
motion

[0] could not open configfile /etc/motion/motion.conf: Permission denied
```

Thanks!

---

### Post by epud on 2011-01-29
I have been playing around with permissions. I have also reinstalled motion. This is weird. Any suggestions?

---

### Post by no2498 on 2011-01-29
try this in a terminal

gstreamer-properties click enter

click video
try v4l and v4l2
click the bottom test button for each 1

if it comes on retry cheese

get the cam working in every thing else before trying skype
skype is a different problem

is a settings thing in the package manager for the philips cams

---

### Post by epud on 2011-01-29
Thanks, but I only get:

```
Video for Linux (v4l): Device "/dev/video0" does not exist.
```

no matter if I choose v4l or v4l2

Could it be that motiond is unloading it and for sone reason unable to reload.

Had I known more linux I might have had a quick look at the kernel logs to figure up why the driver has gone...

---

### Post by no2498 on 2011-01-30
my bad you need to stop motion first

---

### Post by epud on 2011-01-31
I think it was a fault with my webcam itself. I have tried other webcams and they work fine without the /dev/video0 dissapearing. I would recommend people to check before buying a webcam if it works on Ubuntu or not.

---

