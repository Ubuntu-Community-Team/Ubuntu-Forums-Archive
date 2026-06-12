---
title: "turn off internal usb webcam"
date: 2011-04-26
forum: General Help
---

### Post by jonim8or on 2011-04-26
I am trying to use a stereo setup (two Microsoft webcams) on my ubuntu laptop. However, the laptop also has an internal webcam.

I plug my two webcams in ports that belong to different buses
this is what lsusb gives:
```

Bus 003 Device 002: ID 045e:076d Microsoft Corp. 
Bus 002 Device 006: ID 045e:076d Microsoft Corp. 
Bus 002 Device 004: ID 1437:0101  
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 147e:1001 Upek 
Bus 001 Device 003: ID 5986:0343 Acer, Inc 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
one of these webcams works fine, but when I want to open the other one, it fails. For example, when I want to open it with guvcview, I get the following: 
```

vid:045e 
pid:076d 
driver:uvcvideo
checking format: 1448695129
libv4l2: error setting pixformat: Device or resource busy
VIDIOC_S_FORMAT - Unable to set format: Device or resource busy
Init v4L2 failed !! 
ERROR: Minimum Setup Failed.
 Exiting...
VIDIOC_REQBUFS - Failed to delete buffers: Invalid argument (errno 22)
cleaned allocations - 100%
Closing portaudio ...OK
Terminated.

```

When I open gnome-device-manager I see two USB EHCI Controllers in the list, one of which contains the internal webcam, the other contains one microsoft webcam. My guess is that the internal webcam is claiming bandwidth that the microsoft webcam needs.

Is there a way to specifically turn off the internal webcam so that i can use both external ones?

---

### Post by no2498 on 2011-04-26
the only program that you cam use 2 cams with is zone minder
that i know of 

and this may help with the cam 

open a terminal type gstreamer-properties click enter
you can set it to list the cam you would like to use

click video
try v4l and v4l2
use the bottom test button for each 1

---

### Post by jonim8or on 2011-04-28
Then I still get the same: 
```

libv4l2: error turning on stream: Invalid argument
gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video1'. [gstv4l2object.c(1983): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline0/GstV4l2Src:v4l2src1:
system error: Invalid argument]

```

So is there a way of turning off (unmounting or so) the internal webcam?

---

### Post by no2498 on 2011-04-28
with the cam you want to use plugged in and set as the main cam in gstreamer-properties

open a terminal type dmesg click enter

after it stops type lsusb click enter

did dmesg say it found the cam and what driver did it say

---

