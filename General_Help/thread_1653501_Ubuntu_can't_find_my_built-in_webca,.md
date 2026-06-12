---
title: "Ubuntu can't find my built-in webca,"
date: 2010-12-27
forum: General Help
---

### Post by EloRampage93 on 2010-12-27
I have a Dell Inspiron 1525
And for some odd reason I can't use my webcam, whem I try to use my webcam all the programs I tried say the same "webcam/device not found". I don't know what's happening but a while ago I had to reinstall ubuntu 10.10, but the version I had installed before could use my webcam.

I'll be so grateful if someone can help me find the answer!

Regards

---

### Post by Casper35th on 2010-12-27
Try going to Applications>Ubuntu Software Center>Get software and search Jockey-gtk install and see if that fixes the issue.

---

### Post by EloRampage93 on 2010-12-27
It was already installed. I tried reinstalling it but nothing happened.

---

### Post by Quackers on 2010-12-27
What webcam is it? Try looking for a fix for that specific webcam.

---

### Post by mr.farenheit on 2010-12-27
i had the same problem but i got ubuntu to run my camera with the default generated driver. the only thing i did was install Cheese and it worked fine. give that a try.

---

### Post by EloRampage93 on 2010-12-27
> **mr.farenheit said:**
> i had the same problem but i got ubuntu to run my camera with the default generated driver. the only thing i did was install Cheese and it worked fine. give that a try.

The problem is that I knew that my camera wasn't working when I installed Cheese.

---

### Post by KaYnemO on 2010-12-27
> **EloRampage93 said:**
> The problem is that I knew that my camera wasn't working when I installed Cheese.

You know, this may sound very strange, but never hurts to try. Press Fn+F2 key combo and then start cheesy. See if that helps.

---

### Post by EloRampage93 on 2010-12-27
> **KaYnemO said:**
> You know, this may sound very strange, but never hurts to try. Press Fn+F2 key combo and then start cheesy. See if that helps.

Nope! Didn't work.

---

### Post by no2498 on 2010-12-27
try this
click system, preferences
go down the list to multimedia systems selector, start it click video
try v4l and v4l2 click the bottom test button for each 1

hope that helps

---

### Post by IWantFroyo on 2010-12-27
System-Administration-Additional Drivers
It will find your webcam and detect what driver you need, which also works when getting wifi and whatnot. 

Cheese works even if there aren't any drivers listed in the area above with some webcams, like my old veo stingray. It does have a few glitches though, like turning my hair green (which I'm still trying to fix).

---

### Post by EloRampage93 on 2010-12-27
> **no2498 said:**
> try this
click system, preferences
go down the list to multimedia systems selector, start it click video
try v4l and v4l2 click the bottom test button for each 1

hope that helps

It gives me the same error message with both: "Video for Linux (v4l): Device "/dev/video0" does not exist."

---

### Post by tredegar on 2010-12-27
We need to know what the hardware of the webcam is. The output of **lsusb** will probably help here.

Also are there any references to enabling / disabling the webcam in your BIOS?

---

### Post by EloRampage93 on 2010-12-27
> **tredegar said:**
> We need to know what the hardware of the webcam is. The output of **lsusb** will probably help here.

Also are there any references to enabling / disabling the webcam in your BIOS?

I typed "lsusb" and I got this: Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam

The full results are these:

Bus 007 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 007 Device 004: ID 0a5c:4502 Broadcom Corp. Keyboard (Boot Interface Subclass)
Bus 007 Device 003: ID 413c:8126 Dell Computer Corp. Wireless 355 Bluetooth
Bus 007 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. OV2640 Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by EloRampage93 on 2010-12-27
Thanks to the lsusb command I found the name of my camera and found a quick guide that gave me the commands to restart my webcam.

[http://diogomelo.net/drupal/blog/10/webcam-problem-dell-inspiron](http://diogomelo.net/drupal/blog/10/webcam-problem-dell-inspiron)
Here's the link!

And here are the commands.
$ su -
$ rmmod uvcvideo
$ modprobe uvcvideo

---

### Post by no2498 on 2010-12-27
glad you got it working
mark the post as solved
it will help others too

---

