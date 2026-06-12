---
title: "driver or camera issue?"
date: 2010-06-09
forum: General Help
---

### Post by enuckon on 2010-06-09
Hello, 

I couldn't get any signal from my Quickcam 3000 RT with stopmotion.  Is this some sort of a driver issue?  Here is "dmesg" output:

> "
[ 3229.388184] uvcvideo: Found UVC 1.00 device <unnamed> (046d:09a5)
[ 3229.409586] input: UVC Camera (046d:09a5) as /devices/pci0000:00/0000:00:1d.7/usb4/4-1/4-1:1.0/input/input10
[ 3230.420185] 3:3:1: cannot get freq at ep 0x86
[ 3230.684139] uvcvideo: Failed to query (1) UVC control 1 (unit 0) : -110 (exp. 26).
"

What I get is a green screen with stopmotion and vgrabbj.   Are there other ways to create timelapse movies using a v4l2 camera?  

Thanks a lot, 
E.

---

### Post by enuckon on 2010-06-09
I mean, are there v4l2 grabbers whose output could be fed to "stopmotion"?  It looks like "vgrabbj" doesn't get images from camera.  I could get images with "motion" or "Cheese".

---

### Post by no2498 on 2010-06-10
if i read right you would like some thing that takes a pic if it sees motion

wxcam has that
read and install all the page tells you to
comes in a deb file also

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

hope that helps

also cheese you can set the colors in it

---

### Post by no2498 on 2010-06-10
you will need to stop, stop motion only 1 program at a time can use the cam

---

