---
title: "Webcam not working correctly"
date: 2010-10-17
forum: General Help
---

### Post by sathyanmin on 2010-10-17
Hi,

I have Intex IT-305WC webcam for my Ubuntu 10.04 LTS.

My issue is, the webcam is detected by ubuntu, but when i use cheese or skype no video is showing (it shows black screen).

~$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2700 Pixart Imaging, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Can anybody help me out to get the video

---

### Post by AhmetKIRALI on 2010-10-18
I lived this problem. My webcam showed green video. (Model A4Tech PK-635K --> ID 093a:2700 Pixart Imaging, Inc.) 

Try this...
Unplug webcam from usb, and replug. 
If don't work unplug and plug another usb port.
Good Luck...

---

### Post by sathyanmin on 2010-10-18
Thanks for the reply.
But this did not helped. its still showing the black screen

---

### Post by no2498 on 2010-10-19
try doing this and see if it gets better

gstreamer-properties


open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1

cheese has a nice help file look in the faq's

hope this helps

---

### Post by tg3793 on 2011-03-28
Hmm, gstreamer-properties looked promising. I have a Intex 308WC.  I've been attempted to detect the video for the last five minutes with gstreamer-properties but nothing has shown up yet.

Here is my lsusb output:

```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 017: ID 1d0f:2504  
Bus 001 Device 004: ID 4971:ce15 SimpleTech 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

As you can see the Intex is showing up as **ID 1d0f:2504** but there is no name beside it. Just guessing this is a problem.

Thanks for any help you might offer.

---

### Post by no2498 on 2011-03-28
try setting the plugin to auto in gstreamer-properties

also type webcam in a terminal click enter
should load a cam grabber

---

### Post by tg3793 on 2011-03-28
Thanks for the tip. Might be useful for me at some later date or might  be useful for someone else. I tried another web cam (which works great)  and I suspect my Microdia might just be bad ... I'll try the Microdia on  a different computer when I get access to one.

Again thanks.

---

