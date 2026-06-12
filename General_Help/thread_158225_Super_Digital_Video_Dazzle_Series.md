---
title: "Super Digital Video Dazzle Series"
date: 2006-04-10
forum: General Help
---

### Post by sebth on 2006-04-10
I bought a USB Video Tuner/Capture Device named Super Digital Video Dazzle Series. I tought it would be as simple as plug it in and start an application like xawtv, but I was wrong. I never used video capture devices on linux so maybe there are some steps I need to following in order to be able to use it. I tried searching on the Internert for a couple of days but I didn't find anything useful. 

lsusb gives me this info about my device :

Bus 005 Device 004: ID eb1a:2821 eMPIA Technology, Inc.

When I try to start xawtv I get this 

This is xawtv-3.94, running on Linux/i686 (2.6.12-10-686-smp)
WARNING: No DGA support available for this display.
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

If you know anything that could potentially help me please share this information. 

Thank you very much.

---

### Post by trent dillman on 2006-04-10
Do you have a /dev/video? If so, try
```
sudo ln -s /dev/video /dev/video0
```

---

### Post by sebth on 2006-04-10
/dev/video exists but it is a symlink to /dev/video0 . I also have a bunch of other /dev/videoN (from 0 to 63 ) that exists. I tried doing a simple cat /dev/video or cat /dev/video0 but it says "No such device". So from what I understand, the "file" exists but the not the "device"

---

### Post by riteshsarraf on 2006-08-05
> **sebth said:**
> I bought a USB Video Tuner/Capture Device named Super Digital Video Dazzle Series. I tought it would be as simple as plug it in and start an application like xawtv, but I was wrong. I never used video capture devices on linux so maybe there are some steps I need to following in order to be able to use it. I tried searching on the Internert for a couple of days but I didn't find anything useful. 

lsusb gives me this info about my device :

Bus 005 Device 004: ID eb1a:2821 eMPIA Technology, Inc.

When I try to start xawtv I get this 

This is xawtv-3.94, running on Linux/i686 (2.6.12-10-686-smp)
WARNING: No DGA support available for this display.
can't open /dev/video0: No such file or directory
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: No such file or directory
v4l2: open /dev/video0: No such file or directory
v4l: open /dev/video0: No such file or directory
no video grabber device available

If you know anything that could potentially help me please share this information. 

Thank you very much.


There's currently no support for the device in the upstream kernel. I too have the same device.
Thanks to Markus Rechberger, the support has been added for video in the latest mercurial rcs tree at linuxtv.org. I just checked it.
You can get a copy of the source with:
hg clone -R [http://linuxtv.org/hg/~mrechberger/v4l-dvb](http://linuxtv.org/hg/~mrechberger/v4l-dvb)

The audio support will be enabled soon but for that I need to provide him some information which needs to be gathered with that device running on Windows.
If you have that setup, please contact me or Markus.
You know where, irc.freenode.net #em28xx

Cheers!
Ritesh

---

### Post by sebth on 2006-08-17
Thank you for your reply.

I downloaded the latest release and installed it with make && sudo make install .

Now I have the device /dev/video0 but I can't get the tuner to work.

I tried with mythtv and and got these errors in mythbackend.log :

strange error flushing buffer ...
VIDIOCMCAPTUREi0: Invalid argument
VIDIOCMCAPTUREi1: Invalid argument


In the console from where I started mythfrontend, I get these errors : 

2006-08-17 21:00:04.792 Couldn't get the color key color, and we need it.
You likely won't get any video.


I am not sure exactly what you need in order to debug this. Feel free to ask me any question about my system. 

Thank you

P.S. This post is in the Breezy forum but now I am using Dapper.

---

### Post by jenymoen on 2007-02-02
Does anyone now where to find the driver for this, I got it from china, but have lost the driver.

I also have lost the software so if someone knows where to find it I will be very grateful.

---

