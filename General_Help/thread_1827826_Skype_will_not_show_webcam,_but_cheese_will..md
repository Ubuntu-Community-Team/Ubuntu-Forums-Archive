---
title: "Skype will not show webcam, but cheese will."
date: 2011-08-18
forum: General Help
---

### Post by lilo346 on 2011-08-18
When i run skype, it detects my camera , but it work show any picture when i test. In gstreamer-properties testing, it works fine using v4l2. When i use Cheese, it comes up with no problem. Below is the terminal output from my testing. How can i get this to work?

omar@omar-desktop:~$ lsmod | grep videodev
videodev               75143  1 uvcvideo
omar@omar-desktop:~$ gstreamer-properties 
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'
omar@omar-desktop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 18ec:3299 Arkmicro Technologies Inc. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Cpierce on 2011-08-18
This solved the issue for me

[http://ubuntuforums.org/showpost.php?p=8390933&postcount=13](http://ubuntuforums.org/showpost.php?p=8390933&postcount=13)

---

