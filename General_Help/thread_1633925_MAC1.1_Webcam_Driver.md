---
title: "MAC1.1 Webcam Driver"
date: 2010-11-29
forum: General Help
---

### Post by JJJCR on 2010-11-29
hi guys, where to download a webcam driver for macbook? any help is greatly appreciated. Thanks. :D

---

### Post by no2498 on 2010-11-30
most webcams just work now days

try the cam in cheese, full name is cheese webcam booth
if its installed look in sound and video for it

with you on a mac i dont know if you can use this

sudo apt-get install cheese

wit the cam plugged in type lsusb in a terminal click enter
that should give the cam # and name in case you need a driver

hope this helps

---

### Post by JJJCR on 2010-12-01
hi, i had installed the cheese but when tried to run from skype there's an error message..but can't exactly remember the error..any other methods? please help.. Thanks in advance.

and one more thing the cam is built-in on the laptop

---

### Post by no2498 on 2010-12-01
you can try this but i do not think it will work
most that ive seen that try skype say it cant find the cam
gstreamer needs the good,bad,ugly, and 10 installed

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

---

