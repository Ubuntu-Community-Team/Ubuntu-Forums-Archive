---
title: "how to get webcam working?"
date: 2009-11-11
forum: General Help
---

### Post by levis lover on 2009-11-11
i have a sony vaio CS 17G with ubuntu 9.10
i want to know that how can i get my webcam get working?

---

### Post by levis lover on 2010-01-13
anyone?

---

### Post by Tralce on 2010-01-13
Please check to see if Ubuntu can see it at all. Open a terminal, type "lsusb" (no quotes), then copy and paste the result to the forum. 

(Typically the webcam will show up in that list if Ubuntu can see it at all, since most laptop webcams are connected by USB.)

---

### Post by Sef on 2010-01-13
> Please check to see if Ubuntu can see it at all. Open a terminal, type "lsusb" (no quotes), then copy and paste the result to the forum. 

(Typically the webcam will show up in that list if Ubuntu can see it at all, since most laptop webcams are connected by USB.)

Most, but not all, so the op's webcam may not show up at all.

---

### Post by Tralce on 2010-01-13
> **Sef said:**
> Most, but not all, so the op's webcam may not show up at all.

Indeed. Are there any other commands in which the webcam might show up?

---

### Post by levis lover on 2010-01-14
here is the output ::

```
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:183f Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

### Post by Futile10 on 2010-01-25
I have the CS series as well and I cannot use my webcam.  I tried pushing the capture touch buttom but nothing happened.

I have the following output from the terminal:

Bus 007 Device 002: ID 044e:3017 Alps Electric Co., Ltd 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c526 Logitech, Inc. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:183f Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I have no idea what that means?  

Please...someone help me!  I do not want to have to go back to using Winblows...any help???!!!!!

---

### Post by levis lover on 2010-01-29
anybody?

---

### Post by niffcreature on 2010-01-29
try dmesg for all the hardware. 
i believe you can also go to hardware testing from the system administrative menu, and view the report afterwards for something similar.
this will definitely show the webcam as something, but what it will show up as i have no idea.
that would be the first step... maybe.
says here its usb [http://www.linux.com/archive/forums/topic/3859](http://www.linux.com/archive/forums/topic/3859)
maybe this will help : [http://www.linux.com/news/hardware/peripherals/8205-configuring-your-webcam-to-work-under-linux](http://www.linux.com/news/hardware/peripherals/8205-configuring-your-webcam-to-work-under-linux) ?
good luck.
i cant help you anymore, obviously i dont know what im talking about. im just trying to get my vaio z camera to work and its supposed to be supported so its an unrelated issue.

---

### Post by no2498 on 2010-01-29
open a terminal type ( gstreamer-properties ) click video
try v4l1 or v4l2

to see the cam after that you need a program like
cheese or wxcam
1 of the 2 will see your cam

now tins is from cheese


Frequently Asked Questions

    * Cheese Manual

    * 5.1.&#8194;The video is sluggish/has a slow response. What can I do?
    * 5.2.&#8194;I have a Mac with iSight and a ATI graphics card, and the colors are weird.
    * 5.3.&#8194;My webcam works with gstreamer, but does not work with Cheese. What's wrong?
    * 5.4.&#8194;My webcam works with other programs such as Ekiga, Camorama, but not with Cheese. What's wrong?
    * 5.5.&#8194;Where does Cheese store my photos?
    * 5.6.&#8194;My Quickcam Express doesn't work with Cheese...
    * 5.7.&#8194;Which cameras are supported

5.1.&#8195;The video is sluggish/has a slow response. What can I do?


      You may have set "ximagesink" ("X Window System (No Xv)") as video-output.
      This means, that your cpu is doing all the work. Change it to "xvimagesink"
      ("X Window System (X11/XShm/Xv)") in order to let your graphics card do the work.
    


      To change the settings, run "gstreamer-properties", click the Video tab
      and change the appropriate settings.

---

