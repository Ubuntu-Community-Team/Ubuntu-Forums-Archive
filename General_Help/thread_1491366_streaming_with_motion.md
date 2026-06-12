---
title: "streaming with motion"
date: 2010-05-23
forum: General Help
---

### Post by stevepoppers on 2010-05-23
Main problem is that the cam worked for five minutes. A few tweaks later, I get this:
```
[0] Processing thread 0 - config file /home/anthony/.motion/motion.conf
[0] Motion 3.2.11 Started
[0] ffmpeg LIBAVCODEC_BUILD 3412993 LIBAVFORMAT_BUILD 3415808
[0] Thread 1 is from /home/anthony/.motion/motion.conf
[0] motion-httpd/3.2.11 running, accepting connections
[0] motion-httpd: waiting for data on port TCP 8080
[1] Thread 1 started
[1] Failed to open video device /dev/video0: 
[1] Could not fetch initial image from camera
[1] Motion continues using width and height from config file(s)
[1] Resizing pre_capture buffer to 1 items
[1] Started stream webcam server in port 8081
[1] Retrying until successful connection with camera
[1] Failed to open video device /dev/video0: 

```

I remove --purge 'd and reinstalled, but nothing changed. The hard part is that I'm working on a server with no gui, so don't suggest gstreamer or cheese.

---

### Post by no2498 on 2010-05-23
this should help reset the dev's
you can find this in the cheese help faq's
if the cam stops again read cheese help faq's tells you to change the plugin

open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

hope this helps

---

### Post by stevepoppers on 2010-05-23
I don't have a gui. I doubt the server would support it. It's just an old Gateway. It's failed at it before. I just want to pipe video to ...something. I don't know what exactly, yet, but I want to at least have the camera working.

---

### Post by no2498 on 2010-05-23
was just resetting the devs

the cam will not work in cheese if motion is running

---

### Post by no2498 on 2010-05-23
or in gstreamer-properties

---

### Post by stevepoppers on 2010-05-24
If resetting the devs is what needs to be done, tell me how to do it in the terminal. I can't use gstreamer or cheese. I don't have a gui AT ALL. No desktop environment in which to run these things. I have nothing BUT the terminal.

---

