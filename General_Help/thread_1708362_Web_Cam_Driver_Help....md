---
title: "Web Cam Driver Help..."
date: 2011-03-16
forum: General Help
---

### Post by galacticaboy on 2011-03-16
I have what my terminal says is a SiGma Micro USB Webcam, I cannot find a driver for it. It does not work when I just plug it in... its a generic webcam, a little cheepie... but its good. Can someone help me out? Thanks!
David

---

### Post by no2498 on 2011-03-17
open a terminal type in
sudo apt-get install cheese click enter
after installed look in sound and video for it
cheese webcam booth
try the cam in it first
most cam drivers are in the kernel now days

---

### Post by galacticaboy on 2011-03-17
I have Cheese and it tells me it cannot detect a webcam. I have tried everything...

---

### Post by coldraven on 2011-03-17
Buy another web-cam that has UVC in it's description. I think UVC means "Universal Video Class" and will work with no additional drivers.
I bought one for £3 on Ebay, it works fine in Skype.

---

### Post by no2498 on 2011-03-18
look in your package mamager for xawtv install it
it loads a cam grabber

try the cam in xawtv

open a terminal type dmesg click enter
did it find the cam

---

