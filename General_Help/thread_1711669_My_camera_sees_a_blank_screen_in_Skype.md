---
title: "My camera sees a blank screen in Skype"
date: 2011-03-21
forum: General Help
---

### Post by jlib on 2011-03-21
I changed something in Terminal a while back to help make my Logitech QuickCam work with Skype. Unfortunately it didn't help at all.  I looked up my changes in History and this is how it looks.  

 1  sudo gedit /usr/local/bin/skype
    2  sudo chmod a+x /usr/local/bin/skype
    3  apt-get install-f
    4  apt-get install -f
    5  LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

I'm not absolutely sure, but I think line 5 is the problem.  Is there a way to undo this change so I can see if the video will work with Skype?  Or do you have any other suggestions?

My camera works with Cheese, and I have the sound working fine as well. I'm running Ubuntu 10.10 Maverick Meerkat on a Dell.  


Thanks. :)

---

### Post by Script Warlock on 2011-03-22
lsusb

---

### Post by no2498 on 2011-03-22
line 5 should read
LD_PRELOAD=/usr/lib/libv4l/v4l compat.so skype

you had v4l1

we use v4l2 but they have not changed it yet
just leave it at v4l


do this in a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1

---

### Post by jlib on 2011-03-22
Tested, and v4l2 works.  What do I do next?

---

### Post by jlib on 2011-03-22
lsusb still gives me a blank screen when I test in skype from their test page.   Here is my exact camera though: 
Logitech, Inc. QuickCam E2500 series

---

### Post by Script Warlock on 2011-03-22
lsusb display usb infos..

i found the workaround bit outdated [http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/](http://www.actionshrimp.com/2008/08/logitech-quickcam-e2500-on-ubuntu-skype/) if ain't working we'll find another way.

still we need some infos of your cam
lsusb 
lsmod | grep videodev

---

### Post by jlib on 2011-03-23
Bus 002 Device 002: ID 046d:089d Logitech, Inc. QuickCam E2500 series
 lsmod | grep videodev
videodev               43098  1 gspca_main
v4l1_compat            13359  1 videodev

---

