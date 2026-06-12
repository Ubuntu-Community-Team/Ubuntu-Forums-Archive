---
title: "Laptop webcam with Ubuntu"
date: 2010-04-07
forum: General Help
---

### Post by Cityscape on 2010-04-07
Hi,

I'll be helping a friend set his his laptop (hp pavilion) with Ubuntu 9.10 in a few days. What is needed to get his webcam working? And he is a beginner, so what is the best easy to use webcam software that can play what the webcam is seeing without recording, record video from the cam and save then to the hard disk?

---

### Post by no2498 on 2010-04-07
open a terminal type gstreamer-properties click enter
click video try v4l1 and v4l2
click close 

now try the cam in cheese
cheese should be loaded
look in sound & video

hope this helps

---

### Post by Cityscape on 2010-04-07
So you recommend Cheese for the tasks I was asking about?

---

### Post by no2498 on 2010-04-07
you can get wxcam
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

---

### Post by Cityscape on 2010-04-07
Okay so which is better and/or easier to use, Cheese or wxcam? Which do you recommend?

---

### Post by no2498 on 2010-04-07
i myself like wxcam
i can get my cam up and running in 3 seconds in/on 804
2 seconds on my other computer with 910 on it
i pin it to the top panel

---

### Post by no2498 on 2010-04-07
do not uninstall cheese
ubuntu give it all the cam settings

---

### Post by sam-bo on 2010-08-21
Subject:  How to post
Obstacle: lack of knowd
Question: still
Needs: yes
Official Jam:  Indeed.  I have a slight issue with hp dv9408ca built in webcam.  Terminal running; lsusb quotes;

Bus 002 Device 002: ID 046d:c03d Logitech, Inc. M-BT96a Pilot Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ca:1810 Ricoh Co., Ltd Pavilion Webcam [R5U870]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

which is not bad exept cheese nor wxCam display an image.  Both indicate "nodevice found"  or "Cannot open /dev/video0.
Please check if your system has the correct driver for your webcam, or change the webcam device in settings->preferences."

any leads?

thnx

sam

---

### Post by earthpigg on 2010-08-21
hi,

install webcamstudio and try clicking around with that. i've found it to detect webcams that other software (eg, cheese) did not.

---

### Post by sam-bo on 2010-08-22
Webcam Studio: You are not part of the video group!  Make sure that your user is part of the video group for access to the virtual webcam device...

I tried output>video recorder.  playback is blank.

---

### Post by no2498 on 2010-08-22
sam-bo

You are not part of the video group
you need permission its a command like so every one on the computer can use video

and im sorry i do not know it

---

### Post by earthpigg on 2010-08-22
> **sam-bo said:**
> Webcam Studio: You are not part of the video group!  Make sure that your user is part of the video group for access to the virtual webcam device...

I tried output>video recorder.  playback is blank.

system -> admin -> users and groups -> click on a user -> advanced settings -> user privileges -> check the appropriate box

---

### Post by syntek on 2010-08-28
> **sam-bo said:**
> 
Bus 001 Device 002: ID 05ca:1810 Ricoh Co., Ltd Pavilion Webcam [R5U870]


You need to add the r5u87x driver to Ubuntu.

Installation
========
1. sudo add-apt-repository ppa:r5u87x-loader/ppa
2. sudo apt-get update
3. sudo apt-get install r5u87x
4. sudo /usr/share/r5u87x/r5u87x-download-firmware.sh

(Step 1 only works on Ubuntu 9.10 and newer. On older releases you will need to add this PPA to your APT sources manually.)

Supported hardware
================
05ca:1803 Flybook V5
05ca:1810 HP Pavilion Webcam
05ca:1835 Sony Camera VGP-VCC5 (used on Sony Vaio SZ laptops)
05ca:1836 Sony Camera VGP-VCC4 (used on Sony Vaio FE laptops)
05ca:1837 Sony Camera VGP-VCC4 (used on Sony Vaio FZ laptops)
05ca:1839 Sony Camera VGP-VCC6 (used on Sony Vaio CR laptops)
05ca:183a Sony Camera VGP-VCC7 (used on Sony Vaio SZ and TZ11 laptops)
05ca:183b Sony Camera VGP-VCC8 (used on Sony Vaio FZ laptops)
05ca:183e Sony Camera VGP-VCC9 (used on Sony Vaio FZ laptops)
05ca:1841 Fujitsu F01 / Fujitsu Lifebook U810

Note
========
On my HP Pavilion laptop, it works great with Cheese and everything else, but I can't get it to work with Skype. Anyone have any ideas?

---

### Post by sam-bo on 2010-09-09
Thanks, that worked.  My internal wbcam fired right up.  works perfect.

thanks again,

sam

---

