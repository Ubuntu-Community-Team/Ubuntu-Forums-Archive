---
title: "USB tv tuner"
date: 2010-05-24
forum: General Help
---

### Post by meee on 2010-05-24
what do I need to install to get a USB tv tuner working?  I have a generic usb "stick".  It shows up in windows as a 7240 TVBox.  I've tried mythtv, but it doesn't see or show the device.  I am running Ubuntu 9.1.

---

### Post by fragos on 2010-05-24
Try tvtime, it's very good at automatic setup although I've never used it with a USB TV Card.

---

### Post by LowSky on 2010-05-24
with the card plugged in open a terminal and tupe
```
lsusb
```

the model should pop up in that information, if it does, you can then look at finding the drivers for Linux from here:
[http://www.linuxtv.org/](http://www.linuxtv.org/)

afterword you can then use mythtv if you setup the backend correctly

---

### Post by Failboat88 on 2010-05-24
Tuner cards and linux is a pain. Google your card + linux and see if it's compatible. I've been recently putting together a htpc, and I would recommend pchdtv 5500 for linux. It picks up all the types of signals and is built for linux. One more less costly option is Haup. PVR-150/250/500. They are analog (NTSC) only and found on ebay. 

Alternatively, you could just use vista or 7 to get your tuner working. Windows support is much better for tuner cards, and it is very easy to use. I'm not a fan of windows, but their htpc setup is good. Linux is free and viruses are not an issue; so I continue to try and get my htpc working.

---

### Post by meee on 2010-05-24
I tried TVTime and all that comes up is my web cam.  MythTv didn't show the device either.

---

### Post by fragos on 2010-05-24
Your webcam is probably /dev/video0 and you TV /dev/video1. Look in ~./tvtime/tvtime.xml for "V4LDevice". You can change the device there. Note that the assignment of video0 and video1 may be swapped the next time you boot. There's a way around that but 1st lets try this. Tvtime is for TV devices that use the bttv driver. Run "lsmod |grep tv" to see if it's bttv or ivtv.

---

### Post by meee on 2010-05-24
That line does not return anything.  I get another prompt, no output.

---

### Post by fragos on 2010-05-24
Means no driver loaded for bttv or ivtv. There may be a driver I'm not familiar with with. How about "lsmod |grep v4l2"?

---

### Post by meee on 2010-05-24
nothing, just a return to the prompt.

---

### Post by OfficeLinebacker on 2013-02-13
Just wanted to say I dug up an old "Hybrid USB 2.0 TV Stick 7240" from TWINHAN and I was hoping to use it to set up a Mythbuntu box but I guess it's just too Old/cheap/esoteric for there to be a Linux driver for it.

---

