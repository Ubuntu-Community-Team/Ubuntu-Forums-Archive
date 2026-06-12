---
title: "installing a new driver"
date: 2011-07-11
forum: General Help
---

### Post by Allwynd on 2011-07-11
hello, i have a problem, my motherboard has ati radeon 3300 hd and when i install it, after restart, my resolution is automatically changed to something big, and my monitor only supports 1024x768 and if something bigger is selected, the monitor goes NO SIGNAL

so help me out if you can, what am i supposed to do? i have some driver installed by default, i can utilize compiz just fine, play videos on youtube at 1080p just fine, play World of Warcraft almost smooth, i believe that if that driver is installed, it will be even better, but im afraid that if i install it, my resolution will automatically change to something large and my monitor will go NO SIGNAL

---

### Post by pqwoerituytrueiwoq on 2011-07-11
if it goes south you can boot a live cd and ant your /etc/X11/xorg.conf file and force the resolution
it is unlikely it will give you something your monitor does not support
this is what sets the resolution which is auto detect by default
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1600x900_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```i forced it after i took my system out of standby and then turned the monitor and got a signal out of range error on my screen

i had no issue with a radion 3000 integrated gpu detecting resolutions used a vga port did not try dvi/hdmi

---

### Post by Allwynd on 2011-07-12
thanks,i will give this a try

EDIT: actually i tried to vew xorg.conf in normal mode, to see its gonna be easy and when i open with with sudo its empty, i search for "metamodes", but its not giving me any results.. there was a question on another forum that its okay for fedora 10 to be empty as it was no longer using, while ubuntu is still using it.. is 11.04 still using it? what is it that im missing?

---

### Post by Bucky Ball on 2011-07-12
System>Administration>Additional Drivers (or Hardware Drivers). ATI driver there but disabled?

---

### Post by Allwynd on 2011-07-12
this is what i get: 


[[IMG]http://img13.imageshack.us/img13/6189/screenshotxk.th.png[/IMG]]("http://img13.imageshack.us/i/screenshotxk.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")


last time i activated it i was with 10.04 and after restart my monitor went NO SIGNAL

---

### Post by Bucky Ball on 2011-07-12
Well, that is the proprietary ATI driver (their very own) so the choice is yours as to whether you activate it or not. If it gives no signal, boot in using the recovery kernel, choose 'Failsafe X' from the recovery options list which will take you to a low graphics desktop, and deactivate it again.

---

### Post by Allwynd on 2011-07-12
so i gave it a try and it happened just as i thought - no signal, but thanks to you i went into failsafeX and deactivated it.. so i guess ive found partial solution

---

### Post by pqwoerituytrueiwoq on 2011-07-12
xorg be default usually uses auto so there is no xorg.conf file unless you make one 
```
sudo Xorg -configure
```then there will be a xorg.conf file
btw this will force the default driver unless you edit it

---

