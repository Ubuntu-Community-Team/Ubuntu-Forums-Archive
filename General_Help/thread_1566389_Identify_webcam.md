---
title: "Identify webcam"
date: 2010-09-02
forum: General Help
---

### Post by J V on 2010-09-02
How do I identify a webcam in ubuntu? I forgot what model I'm using... It's USB of course, I know its at bus 2 device 2 (From lsusb) but I can't seem to find anything more than that...

---

### Post by howefield on 2010-09-02
> **J V said:**
> How do I identify a webcam in ubuntu? I forgot what model I'm using... It's USB of course, I know its at bus 2 device 2 (From lsusb)

Do you get something like this from lsusb ?

> Bus 002 Device 004: ID 046d:09a4 Logitech, Inc. QuickCam E 3500

Using the ID string "046d:09a4" to search for more information gives me...

[http://www.ideasonboard.org/uvc/](http://www.ideasonboard.org/uvc/)

from where I can see it should work perfectly, as indeed it does.

---

### Post by J V on 2010-09-02
Ah, thanks! Don't suppose you'd know where I could find out weather a "Logitech webcam C200" is hardwired to show the LED when active? Just want to put my mind at ease... I know linux is near-impregnible but swiveling it round all the time is annoying ;P

---

