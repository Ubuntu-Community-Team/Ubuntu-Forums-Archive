---
title: "Setting up motion webcam and /dev/video0"
date: 2010-05-07
forum: General Help
---

### Post by berlinbrown on 2010-05-07
```
I was trying to setup motion, the web capture software.  I just put a basic Logitech device in the usb port.  I installed the cheese application and can see the video from the device through that application.

When I use "motion" and use /dev/video0, I get the following messages:

http://paste.lisp.org/display/98937


Does anyone have experience with motion?

[1] Using V4L1
[1] Resizing pre_capture buffer to 1 items
[1] sync error in proc 2759: 
[1] mcapture error in proc 2759: 
[1] Video device fatal error - Closing video device
[1] Closing video device /dev/video0
[1] Retrying until successful connection with camera
[1] cap.driver: "STV06xx"
[1] cap.card: "Camera"
[1] cap.bus_info: "usb-0000:00:10.1-1"
[1] cap.capabilities=0x05000001
[1] - VIDEO_CAPTURE
[1] - READWRITE
[1] - STREAMING
[1] Supported palettes:
[1] 0: GRBG (GRBG)
[1] Unable to find a compatible palette format.
[1] Using VIDEO_PALETTE_YUV420P palette
[1] Using V4L1
[1] sync error in proc 2759: 
[1] mcapture error in proc 2759: 
[1] Video device fatal error - Closing video device
[1] Closing video device /dev/video0
^C[1] Thread exiting

```

---

### Post by no2498 on 2010-05-08
see if you have this installed

libv4l/v4l1compat.so

its some thing like that in the package manager

if not wxcam may load it has motion also

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

read and install all the page tells you to do

hope this helps

---

### Post by no2498 on 2010-05-08
just reread your ?

you do not have the cam working at all

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

try the cam in cheese webcam booth

it should be loaded in sound&video

---

### Post by berlinbrown on 2010-05-08
It does work with cheese.  But I get the /dev/video0 error with motion.

I have the v4l1compat.so  v4l2convert.so  

drivers.

---

### Post by berlinbrown on 2010-05-08
click video try v4l1 and v4l2
click the bottom test button for each 1


I tried both of these, they both work.

---

### Post by no2498 on 2010-05-08
you need to just try 1 or the other till 1 works

you may try changing the plug in also

look in the cheese help faQ's

see if you can install wxcam  

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

it has motion

---

### Post by no2498 on 2010-05-08
ok im slow tonight sorry

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so (program name you would like to use here)
no ( )

---

### Post by berlinbrown on 2010-05-11
no ( )

What does this mean?

---

### Post by no2498 on 2010-05-12
do not use them

---

### Post by heroedeleyenda on 2011-07-31
Hello,
I had a similar problem using my USB Logitech Quickcam chat in /dev/video1 (I have a tuner in vide0).

The answer proposed by no2498 (export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so) solved my problem. Thank you.

For more details:


# /usr/bin/motion
[0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Motion 3.2.12 Started
[0] ffmpeg LIBAVCODEC_BUILD 3426306 LIBAVFORMAT_BUILD 3424258
[0] Thread 1 is from /etc/motion/motion.conf
[0] motion-httpd/3.2.12 running, accepting connections
[0] motion-httpd: waiting for data on port TCP 8080
[1] Thread 1 started
[1] cap.driver: "spca561"
[1] cap.card: "Camera"
[1] cap.bus_info: "usb-0000:00:02.0-1"
[1] cap.capabilities=0x05000001
[1] - VIDEO_CAPTURE
[1] - READWRITE
[1] - STREAMING
[1] Config palette index 8 (YU12) doesn't work.
[1] Supported palettes:
[1] 0: S561 (S561)
[1] 1: GBRG (GBRG)
[1] Unable to find a compatible palette format.
[1] ioctl (VIDIOCGCAP): Invalid argument
[1] Could not fetch initial image from camera
[1] Motion continues using width and height from config file(s)
[1] Resizing pre_capture buffer to 1 items
[1] Started stream webcam server in port 8081
[1] Retrying until successful connection with camera
[1] cap.driver: "spca561"
[1] cap.card: "Camera"
[1] cap.bus_info: "usb-0000:00:02.0-1"
[1] cap.capabilities=0x05000001
[1] - VIDEO_CAPTURE
[1] - READWRITE
[1] - STREAMING
[1] Config palette index 8 (YU12) doesn't work.
[1] Supported palettes:
[1] 0: S561 (S561)
[1] 1: GBRG (GBRG)
[1] Unable to find a compatible palette format.
[1] ioctl (VIDIOCGCAP): Invalid argument
[1] Retrying until successful connection with camera
[1] cap.driver: "spca561"                                                                                                                                                                                                                    
[1] cap.card: "Camera"                                                                                                                                                                                                                       
[1] cap.bus_info: "usb-0000:00:02.0-1"                                                                                                                                                                                                       
[1] cap.capabilities=0x05000001                                                                                                                                                                                                              
[1] - VIDEO_CAPTURE                                                                                                                                                                                                                          
[1] - READWRITE                                                                                                                                                                                                                              
[1] - STREAMING                                                                                                                                                                                                                              
[1] Config palette index 8 (YU12) doesn't work.                                                                                                                                                                                              
[1] Supported palettes:                                                                                                                                                                                                                      
[1] 0: S561 (S561)                                                                                                                                                                                                                           
[1] 1: GBRG (GBRG)                                                                              
[1] Unable to find a compatible palette format.                                                                                                               
[1] ioctl (VIDIOCGCAP): Invalid argument                                                                                                                   
... etc ...

gstreamer-properties and cheese test were OK, but
the lsof -p motionPid were not showing /dev/video1

Solution:

# LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/motion
[0] Processing thread 0 - config file /etc/motion/motion.conf
[0] Motion 3.2.12 Started
[0] ffmpeg LIBAVCODEC_BUILD 3426306 LIBAVFORMAT_BUILD 3424258
[0] Thread 1 is from /etc/motion/motion.conf
[0] motion-httpd/3.2.12 running, accepting connections
[0] motion-httpd: waiting for data on port TCP 8080
[1] Thread 1 started
[1] cap.driver: "spca561"
[1] cap.card: "Camera"
[1] cap.bus_info: "usb-0000:00:02.0-1"
[1] cap.capabilities=0x05000001
[1] - VIDEO_CAPTURE
[1] - READWRITE
[1] - STREAMING
[1] Test palette YU12 (320x240)
[1] Using palette YU12 (320x240) bytesperlines 320 sizeimage 115200 colorspace 00000008
[1] found control 0x00980903, "Hue", range 1,127 
[1]     "Hue", default 64, current 64
[1] found control 0x00980910, "Gamma (software)", range 500,3000 
[1]     "Gamma (software)", default 1000, current 1000
[1] found control 0x00980911, "Exposure", range 1,2372 
[1]     "Exposure", default 700, current 645
[1] found control 0x00980912, "Auto Gain (software)", range 0,1 
[1]     "Auto Gain (software)", default 1, current 1
[1] found control 0x00980913, "Gain", range 0,255 
[1]     "Gain", default 63, current 63
[1] mmap information:
[1] frames=4
[1] 0 length=16777216
[1] 1 length=16777216
[1] 2 length=16777216
[1] 3 length=16777216
[1] Using V4L2
[1] Resizing pre_capture buffer to 1 items
[1] Started stream webcam server in port 8081

-> localhost:8081  ok :-)

So I added the 2 following lines to /etc/init.d/motion

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
export LD_PRELOAD

Thank you again :-)

---

### Post by jobjol on 2011-09-18
Where to put those lines in /etc/init.d/motion?

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
export LD_PRELOAD

---

### Post by no2498 on 2011-09-18
you need to make it a bin bash file like this
#!/bin/bash
          LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
          /usr/bin/skype

---

