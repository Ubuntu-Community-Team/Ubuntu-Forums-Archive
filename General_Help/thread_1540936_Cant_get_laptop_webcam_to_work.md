---
title: "Cant get laptop webcam to work"
date: 2010-07-28
forum: General Help
---

### Post by X-Windows on 2010-07-28
I've been trying to get my built-in webcam to work for the past few hours and am completely stuck... Apparently I need a driver called uvcvideo, but I cant find it anywhere (its repos have been removed). I have installed Cheese and Camorama, neither of which work. Camorama throws this error when launched - "Could not connect to video device /dev/video0). Please check connection. Cheese launches, turns camera light on, shows a black screen for ~1 sec then closes.

The only way I can get the webcam to work is with a program called "guvcview" (light turns on and I can see preview), that's why I'm thinking I need the uvcvideo driver.

I've found various posts on how to install the uvcvideo driver, but I get an error on all its reposotory links - "reposotory not found". I also can't figure out how to install the EasyCam program, yet another repository error.

Does anyone know how to get built-in webcams working? I suspect it is due to my lack of driver, but I could be wrong. Lsusb detects the webcam as a Chicony Electronics Co. LTD Gateway USB 2.0 Webcam, so the kernel detects it, just no apps.

---

### Post by dino99 on 2010-07-28
have you opened synaptic and searched "webcam" and/or "uvc"?

uvcvideo driver is included into kernel since 2.6.26-rc9, but might install v4l2ucp

---

### Post by RabbitWho on 2010-07-28
Google sent me here: [http://slackbuilds.org/repository/13.1/multimedia/guvcview/](http://slackbuilds.org/repository/13.1/multimedia/guvcview/)

I take it you've tried that already?

---

### Post by no2498 on 2010-07-28
try this program wxcam
your webcam is working you said that

read and install all the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

if it stops working at some point do this

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

hope this helps

---

