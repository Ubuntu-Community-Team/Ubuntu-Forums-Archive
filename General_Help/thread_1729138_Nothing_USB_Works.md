---
title: "Nothing USB Works"
date: 2011-04-14
forum: General Help
---

### Post by DaveS4 on 2011-04-14
Hey All, 
   I did another post before and found no help. So let's try this again...

   I installed Ubuntu a few weeks ago and now, It looks like I can't get anything to work through my USB ports. Thumb Drives, extermal hard drive, iPod.... nothing works. 
   When I first got ubuntu, I was able to get a few things to work, but then it just stopped. 

Any ideas??
Thanks in advance, 
Dave

---

### Post by K_45 on 2011-04-14
Is this a desktop or laptop? Boot off the Ubuntu live CD and see if the ports work there.

---

### Post by DaveS4 on 2011-04-14
> **K_45 said:**
> Is this a desktop or laptop? Boot off the Ubuntu live CD and see if the ports work there.

Laptop. 
Good advice! Hadn't thought of that. 

Thanks
-Dave

---

### Post by DaveS4 on 2011-04-15
> **K_45 said:**
> Is this a desktop or laptop? Boot off the Ubuntu live CD and see if the ports work there.

OK, so I booted off of a live cd, and the USB port works fine. 

What do I do?

Thanks
-Dave

---

### Post by DaveS4 on 2011-04-15
Oh, and some info....

I'm working on a dell laptop - about 2 years old. 
Ubuntu 10.10

---

### Post by K_45 on 2011-04-15
Post the output of lsusb in between the code tags.

---

### Post by DaveS4 on 2011-04-15
> **K_45 said:**
> Post the output of lsusb in between the code tags.

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. Wireless 370 Bluetooth Mini-card
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. Integrated Touchpad / Trackstick
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. Integrated Keyboard
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05ca:18a1 Ricoh Co., Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ac:1261 Apple, Inc. iPod Classic
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```


That's just with my iPod connected.

---

### Post by K_45 on 2011-04-15
I've found this thread, which may help:

[http://ubuntuforums.org/showthread.php?t=854684](http://ubuntuforums.org/showthread.php?t=854684)

Have you installed anything recently?

---

### Post by DaveS4 on 2011-04-15
> **K_45 said:**
> I've found this thread, which may help:

[http://ubuntuforums.org/showthread.php?t=854684](http://ubuntuforums.org/showthread.php?t=854684)

Have you installed anything recently?

I've only been using ubuntu for a few weeks now. I have very few things installed. Just skype, banshee, gtkpod, chrome, and eclipse. 

Another thing that doesn't work is the new printer that I just got. Doesn't work at all. 

So iPod has never worked, 
printer has never worked, 
external hard drive I was able to work once, but I mounted it manually, 
flash drives *usually* don't work. 

It's got to be the USB right??

-Dave

---

### Post by K_45 on 2011-04-15
Open up a terminal and run 

```
gksu gedit /etc/modules
```

then add usbhid on one line, and hid on another line as the file says. Save. Reboot. Result?

---

### Post by DaveS4 on 2011-04-15
> **K_45 said:**
> Open up a terminal and run 

```
gksu gedit /etc/modules
```

then add usbhid on one line, and hid on another line as the file says. Save. Reboot. Result?

I ran that first command and got this.....

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc

```


I didn't understand what your instructions said after that. What does this mean?

Thanks 
Dave

---

### Post by K_45 on 2011-04-15
After rtc, press enter and on a new line enter usbhid, then on another line enter usb, as the file says. Then save and reboot.

---

### Post by DaveS4 on 2011-04-16
> **K_45 said:**
> After rtc, press enter and on a new line enter usbhid, then on another line enter usb, as the file says. Then save and reboot.

On that second line, should I type "hid" or "usb"?  
You said "hid", but the first guy said "usb".

---

### Post by K_45 on 2011-04-16
Like so:
 
lp
rtc
usb
usbhid
 
Save and reboot.

---

### Post by DaveS4 on 2011-04-18
K I did that, and it still doesn't work. Printer and ipod don't work. 

-Dave

---

### Post by DaveS4 on 2011-04-19
nobody??

---

### Post by DaveS4 on 2011-04-20
......

---

### Post by DaveS4 on 2011-04-20
.....

---

### Post by DaveS4 on 2011-04-21
Alright last try. 

   I'm also a beginner android developer, and I'm trying to get my current project on to my android device. 
   So I can't print anything, I can't update my ipod, and I can't make any progress on my android projects until my USB problem is fixed. 
   Can anyone help please? 

Thanks
-Dave

---

