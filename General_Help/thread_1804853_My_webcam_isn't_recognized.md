---
title: "My webcam isn't recognized"
date: 2011-07-15
forum: General Help
---

### Post by emurad on 2011-07-15
Hello,

I have a webcam but when I installed Cheese it's as if I don't have it plugged in.

Please help.

---

### Post by ~!geek!~ on 2011-07-15
Use some sort of hardware info script to get the details of all the hardware being detected by the Linux Kernel. I prefer using hwinfo. You can install it using 
> sudo apt-get install hwinfo

This command will give huge amount of output. You can use grep command to get relevant device you are looking for cam or something. This way you will come to know whether your device is even ready to work and just not able to work because of some other problem.

---

### Post by gandaran on 2011-07-15
> **emurad said:**
> Hello,

I have a webcam but when I installed Cheese it's as if I don't have it plugged in.

Please help.
type in terminal
```
gstreamer-properties
```
then test the different video plugins available, maybe your camera will work with one of them, if not you'll have to try get and install drivers.

---

### Post by no2498 on 2011-07-15
look in your package manager for xawtv install it
now in a terminal type dmesg click enter
after it stops close the terminal
try the cam in xawtv

hope this helps

---

