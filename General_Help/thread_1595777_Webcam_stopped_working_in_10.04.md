---
title: "Webcam stopped working in 10.04"
date: 2010-10-13
forum: General Help
---

### Post by ki4jgt on 2010-10-13
I've upgraded to 10.10. Before I did in 10.04 my webcam stopped working. I have an Acer AspireOne netbook ZG5 model. I want to use mousetrap with my webcam, so I would really like to have it back.

---

### Post by ki4jgt on 2010-10-13
O and it is picking me up very slightly. I can see my head moving, but it's all blurred out, as if 

If you look really close at the gray box, you can see the outline of my head. My camera is available, but not all the way!

---

### Post by ki4jgt on 2010-10-14
FOUND THE PROBLEM. CAN SOMEONE GIVE ME THE SOLUTION?

INSTALLED ODESK
DEFAULT ACER CRYSTAL EYE CAM DOESN'T WORK
HOWEVER WHEN DEFAULT IS CHANGED TO DEV/VIDEO0 ACER CRYSTAL EYE CAM IT WORKS FINE

How do I set the default to Video0?

---

### Post by no2498 on 2010-10-15
i know this is NOT how you do it but i can change mine in this program wxcam

read and install all the page tells you to

[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

---

### Post by MaheshChowta on 2010-11-10
I've installed 10.10. I have an Acer Aspire 4710z. Ubuntu is not detecting Bluetooth and Webcam.

gstreamer - properties shows following error:

gstreamer-properties-Message: Error running pipeline 'Video for Linux 2 (v4l2)': Error starting streaming on device '/dev/video0'. [gstv4l2object.c(1983): gst_v4l2_object_start_streaming (): /GstPipeline:pipeline8/GstV4l2Src:v4l2src5:
system error: Invalid or incomplete multibyte or wide character]

I tried, cheese and wxcam, but no avil.

---

### Post by no2498 on 2010-11-10
MaheshChowta

try this in a terminal type, webcam click enter
did it install a webcam grabber 

also gstreamer needs these installed good,bad,ugly, and 10

---

### Post by ki4jgt on 2010-11-10
When I installed UNR it fixed it, but it broke audacity. LOL now I have not menus in audacity. when I'm in desktop edition.

---

### Post by MaheshChowta on 2010-11-11
thanks no2498

I tried webcam and it gave following error;

mahesh@mahesh:~$ webcam
reading config file: /home/mahesh/.webcamrc
video4linux webcam v1.5 - (c) 1998-2002 Gerd Knorr
grabber config:
  size 320x240 [none]
  input (null), norm (null), jpeg quality 75
  rotate=0, top=0, left=0, bottom=240, right=320
libv4l2: error turning on stream: Invalid or incomplete multibyte or wide character
libv4l2: error reading: Invalid argument
v4l2: read: Invalid argument
capturing image failed

But after this, if I run Cheese, I can get images from webcam. If I close and restart the Cheese, I will not get the images. If I run webcam in terminal again and try cheese, i will get images. 

Any how, thanks for the help.

---

