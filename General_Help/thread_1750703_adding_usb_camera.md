---
title: "adding usb camera"
date: 2011-05-05
forum: General Help
---

### Post by gehad saad on 2011-05-05
i've a system relies on Linux version 2.6 
i need to add  a  usb camera for this system as it supports somekind of cams 
wich i doesn't need .
shall i need to add module & driver & may HAL and recompile kernel again !?
i'm using ubuntu10.10 which i use it to recompile kernel for this system

---

### Post by gehad saad on 2011-05-06
can any one help me ?

---

### Post by deathadder on 2011-05-06
By USB camera I take it you mean a web cam? If you can tell us the make and model it'll help...

---

### Post by no2498 on 2011-05-06
open a terminal type dmesg click enter
after it stops type lsusb click enter
that should give a number and name of your cam

install cheese try the cam in cheese

---

### Post by gehad saad on 2011-05-06
i mean that i have a system relies on linux version2.6 
this system works on some board
this board has a sensor for camera 
so the system  has a camera modules & driver" for cam related to the sensor "already built in " from system user guide"
but i didn't need this camera 
i need another one which can work on USB port 
how can i know the drivers & modules already built in this system for cams?
and how to add these ?
" i  don't have any camera yet i search for camera driver which i can install on this rare system then i'll buy the cam "

---

### Post by no2498 on 2011-05-07
open a terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
set it to the cam you like to use and test it

---

### Post by gehad saad on 2011-05-10
may i know the steps for adding anew hardware for linux system 
sure new h.w means non built in .
from scratch !

---

