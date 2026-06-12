---
title: "An interesting use of the webcam."
date: 2011-05-25
forum: General Help
---

### Post by yay101 on 2011-05-25
Hey all!

First of all I'm a long term user and not afraid to get into the console and text editing to get results. I come to you all with an issue and a question.

1. My webcam displays nothing but black, sound works fine but no application can get anything but a straight black signal from it as for video. Gstreamer config program also lists it as default and only feeds as a black screen also so its not an application problem. 

[http://www.logitech.com/en-us/webcam-communications/webcams/devices/5865](http://www.logitech.com/en-us/webcam-communications/webcams/devices/5865)

That is the exact webcam (C200 from logitech).

It used to work fine in 10.04/10.10 so im unsure what has caused it other than a new bug, if so i will post one.

2. The second thing is an idea i have to assist with using 3 monitors very efficiently, i would like to use head tracking software to move my mouse to the corresponding screen at the corresponding location, for example if my mouse is at 1000 500 and i look to the monitor to the right of the current one i am focusing on it would simply update the cursors location with a +1920 to the x co-ord.

I dont see this being that hard given where tracking is in linux systems, the only problem is A. The webcam issue. And B. how do i pipe the "current monitor" to a script to move the mouse?

My next step is taking this to the devs of such software and asking them as a feature request, what do you guys think?

---

### Post by nemilar on 2011-05-25
Just wondering, have you confirmed that the webcam itself isn't broken (actually sending solid black)?  Plugging it into a different computer, etc...?

---

### Post by tgalati4 on 2011-05-25
There are some head-tracking videos on youtube using Wiimotes or other devices.  That might be a starting point.

What is the module that gets loaded for the webcam when you plug it in?

lsmod

What does dmesg say after you plug it in?

dmesg | tail

---

### Post by no2498 on 2011-05-26
you may install v4l2ucp it is the only thing i can set my cam with
it comes up in system/preferences as video4linux control panel

hope it helps

---

### Post by yay101 on 2011-06-01
Thanks for the quick replies guys/gals. I was expecting emails when replys were posted but it didn't happen haha.

Anyway, webcam works fine under windows (both audio and video). So I'm sure its not a broken webcam.

The top modules after plugin are:

```
uvcvideo               72195  0 
snd_usb_audio         112426  1 
videodev               82052  1 uvcvideo
snd_usbmidi_lib        25139  1 snd_usb_audio
v4l2_compat_ioctl32    17078  1 videodev
```

This is the entire tail:

```
[16532.573484] type=1400 audit(1306944333.659:19): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=25245 comm="apparmor_parser"
[16532.574561] type=1400 audit(1306944333.659:20): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=25245 comm="apparmor_parser"
[18146.300296] CE: hpet increased min_delta_ns to 152727 nsec
[20955.580108] usb 2-1: new high speed USB device using ehci_hcd and address 5
[20956.458906] Linux video capture interface: v2.00
[20957.200503] usbcore: registered new interface driver snd-usb-audio
[20957.200521] uvcvideo: Found UVC 1.00 device <unnamed> (046d:0802)
[20957.290480] input: UVC Camera (046d:0802) as /devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input8
[20957.290623] usbcore: registered new interface driver uvcvideo
[20957.290628] USB Video Class driver (v1.0.0)
```

I have used wiimotes with ubuntu before, so I might give that a go also, thanks.

Thankyou to all of you for your input.

---

### Post by yay101 on 2011-06-03
Bump.

---

### Post by wgarcia on 2011-06-03
You have the webcam plugged in a USB hub? Mine was plugged in a USB hub and working with 10.10, but in 11.04 stopped working. When I plugged it in directly into a USB port it started working again. Take also into account that some computers have a USB hub on the back (a number of USB connections all together) and a direct connection on the front, my webcam started working again when I plugged it in on the front.

I reported this as a bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/788233](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/788233)

If anybody is affected by this and wants to add more information or check "this bug affects me too".

---

### Post by yay101 on 2011-06-03
Sadly its not something so simple for me, it doesnt work in any ports, not even my usb3.0 ones.

---

### Post by no2498 on 2011-06-03
start cheese click edit preference see if you can set the brightness

---

### Post by wgarcia on 2011-06-04
Another suggestions just in case you haven't tried it, from a terminal enter "gstreamer-properties" and in the "video" tab try the different options found there.

---

