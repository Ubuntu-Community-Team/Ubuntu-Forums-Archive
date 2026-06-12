---
title: "help with webcam"
date: 2010-07-29
forum: General Help
---

### Post by tal32123 on 2010-07-29
I have a logitech quickcam deluxe for notebooks and it doesnt show up on my computer please help me :(

---

### Post by no2498 on 2010-07-29
have you tried it in cheese
look in soud and video for cheese webcan booth
most webcam's just work now days

---

### Post by tal32123 on 2010-07-29
> **no2498 said:**
> have you tried it in cheese
look in soud and video for cheese webcan booth
most webcam's just work now days

i tried it in skype it doesnt show up there, neither does the microphone (both the webcam and mic work through the usb)

---

### Post by tal32123 on 2010-07-29
> **tal32123 said:**
> i tried it in skype it doesnt show up there, neither does the microphone (both the webcam and mic work through the usb)

yeah it says no device found in cheese

---

### Post by samijam on 2010-07-29
try running (in terminal or Ctrl-F2) gstreamer-properties and see if you can select your camera in there.  There are options for audio as well, which will let you choose your microphone. 

I don't know about anything Skype-specific though.

---

### Post by tal32123 on 2010-07-29
> **samijam said:**
> try running (in terminal or Ctrl-F2) gstreamer-properties and see if you can select your camera in there.  There are options for audio as well, which will let you choose your microphone. 

I don't know about anything Skype-specific though.

i tried that it doesnt work, i need the drivers for the camera.

---

### Post by no2498 on 2010-07-30
he pointed you the right way 

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

also look in applications, add/remove 
see if gstreamer, good,bad,ugly and 10 is installed

---

### Post by tal32123 on 2010-07-30
> **no2498 said:**
> he pointed you the right way 

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

also look in applications, add/remove 
see if gstreamer, good,bad,ugly and 10 is installed

it tells me device does not exist or cannot identify device. :(

---

### Post by no2498 on 2010-07-31
in gstreamer-properties try changing the plugin

it may or may not help

i just today started seeing that the uvc driver is not loading

that may be what you need

---

### Post by deserthowler on 2010-07-31
Go to the terminal and try:

lsusb 

to see if it finds the camera or not.

Earl

---

### Post by no2498 on 2010-07-31
just started seeing the uvc driver is not loading up right
may be what he needs

---

### Post by tal32123 on 2010-07-31
> **no2498 said:**
> just started seeing the uvc driver is not loading up right
may be what he needs

how would i get that, and on lsusb it doesnt show up

---

### Post by deserthowler on 2010-08-02
I was given a used Logitech 1.3 Megapixel camera today because it quit working in Windows.  I plugged it and ran lsusb.  It showed up.  I downloaded and installed cheese.  I opened cheese and was trying to figure out what to do next when I had a picture.

This is the result of lsusb:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 046d:09a1 Logitech, Inc. QuickCam Communicate MP/S5500
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Have you tried your USB port with another device?
Have you tried the camera on another computer?
Is this an older machine?

You didn't mention so I'm just trying the obvious.  No offense intended.

Earl

---

### Post by tal32123 on 2010-08-02
I haven't tried it on a different computer and I haven't tested the USB port in ubuntu mainly because the camera (logitech quickcam deluxe for notebooks) worked on that USB port in windows. My computer is about 3-4 years old but it runs fine. And no offense taken :)

---

### Post by no2498 on 2010-08-02
open a terminal put this lsusb  in it click enter lsusb
try with the cam plugged in and not
that way you can tell if it finds it or not

---

