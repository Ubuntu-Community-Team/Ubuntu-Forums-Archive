---
title: "Cannot get USB devices to work with Sun VirtualBox"
date: 2009-10-18
forum: General Help
---

### Post by anthony62490 on 2009-10-18
First off, I am not using the OSE Virtualbox, so I know that USB devices are supported. I have been scouring Google for the better part of three days for a working solution, but no luck. I found [THIS]("http://www.samlesher.com/ubuntu/virtualbox-with-usb-support-on-ubuntu") page that told me to add this line to the end of "/etc/fstab"
```
none /proc/bus/usb usbfs devgid=124,devmode=664 0 0
```
But I'm seeing no changes. I have USB devices enabled in my VM settings and I have added myself into the group, "vboxusers"

Any of you know if I have skipped a step?

I am running Ubuntu Jaunty and
"Sun Virtualbox version 3.0.8 r53138" running Windows XP Home Edition

---

### Post by howefield on 2009-10-18
Don't think you need the fstab bit with Jaunty, but shouldn't hurt either. With Jaunty all I ever had to do was add the user to the vbox group and then add the filters to the settings. 


Have you gone through chapter 3.7.9.1 USB settings of the Virtualbox manual. It is short and will only take a few minutes, and is available here...

[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by diablo75 on 2009-10-18
In case you haven't done it yet, you will need to restart Ubuntu completely in order for the changes you made to your fstab file to take effect.

Also, I've used this line in the past:

```
none /proc/bus/usb usbfs devgid=46,devmode=666 0 0
```

You might try it out instead of the one you used to see if it makes a difference.  Good luck!

---

### Post by KlinerDraken on 2009-10-18
In the settings of your VM, did you go to the USB section and add the USB device(s) you want to use in your VM? 

"USB Device Filters"

---

### Post by anthony62490 on 2009-10-21
Okay, I found out how to get them to connect. I had to go to the VM menu and select which USB devices to connect. I'll work out how to mount them automatically later. Thanks, guys!

---

### Post by P4man on 2009-10-21
if you want to connect USB drives this way, I would suggest sharing them across a virtual network instead. Create a network share in virtualbox and access them in windows through:

\\vboxsvr\name-of-share

---

