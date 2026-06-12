---
title: "low frame rate glxspheres in 12.04 (optimus)"
date: 2012-04-26
forum: General Help
---

### Post by yeyoya on 2012-04-26
Hi I  have a Dell xps 14z with a 1 GB NVIDIA® GeForce® GT 520M-graphics card  with Optimus. For that reason I have previously (11.10) installed bumblebee to make use of  the Optimus technology. 

Before when I run glxspheres on 11.10 without 'optirun' I had a framerate of about 60. But now after I have upgraded to Ubuntu 12.04 the frame rate have decreased to about 2-3.

It looks just like in this youtube clip: [http://www.youtube.com/watch?v=6xm5aA46Ofc](http://www.youtube.com/watch?v=6xm5aA46Ofc)

So now I wonder if anyone else have got this problem and if someone knows a work around to increase the frame rate again ?
thanks in advance

---

### Post by imachavel on 2012-04-26
lsb_release
LSB Version:    core-2.0-ia32:core-2.0-noarch:core-3.0-ia32:core-3.0-noarch:core-3.1-ia32:core-3.1-noarch:core-3.2-ia32:core-3.2-noarch:core-4.0-ia32:core-4.0-noarch

this is my release, so you didn't upgrade to ubuntu version 12? Ok so what drivers have you got going, please open terminal with ctrl + alt + t and type this in:

lspci

does the nvidia site give you an option to download a linux driver for .rpm? well no rpm is a different kernel. How about upgrading a windows driver for windows 7 and seeing if it will install as a restricted driver? Ok we'll come back to all that nonsense after you verify lspci

now I don't have the same gpu as you do, but in terminal open glx gears, and post the first 4 captured frame rates so we can compare? My gpu is healthy, want to make sure your hardware memory is caching and processing properly, you could always run a mem test in the bios at boot. But here are the first 4 frame rate replies from glx gears in my linux terminal:

glxgears
7587 frames in 5.0 seconds = 1517.247 FPS
6504 frames in 5.0 seconds = 1300.646 FPS
8119 frames in 5.0 seconds = 1623.716 FPS
8354 frames in 5.0 seconds = 1670.766 FPS

---

