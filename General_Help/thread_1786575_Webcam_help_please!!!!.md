---
title: "Webcam help please!!!!"
date: 2011-06-19
forum: General Help
---

### Post by mj123094 on 2011-06-19
I ran dmesg |grep -i video and i got 


[    0.414566] pci 0000:01:00.0: Boot video device
[   14.437970] Linux video capture interface: v2.00
[   14.457029] uvcvideo: Found UVC 1.00 device Monitor Webcam (SP2208WFP) (05a9:2643)
[   14.470944] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[   14.473856] usbcore: registered new interface driver uvcvideo
[   14.473859] USB Video Class driver (v1.0.0)
[ 5655.424018] usbcore: deregistering interface driver uvcvideo
[ 5667.974218] Linux video capture interface: v2.00
[ 5667.979518] uvcvideo: Found UVC 1.00 device Monitor Webcam (SP2208WFP) (05a9:2643)
[ 5667.982063] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[ 5667.983062] uvcvideo: Failed to query (129) UVC probe control : -32 (exp. 26).
[ 5667.983066] uvcvideo: Failed to initialize the device (-5).
[ 5667.983115] usbcore: registered new interface driver uvcvideo
[ 5667.983118] USB Video Class driver (v1.0.0)


I do not know how to get my webcam working please help!!

---

### Post by no2498 on 2011-06-20
in a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

now install guvcview try the cam in it

---

