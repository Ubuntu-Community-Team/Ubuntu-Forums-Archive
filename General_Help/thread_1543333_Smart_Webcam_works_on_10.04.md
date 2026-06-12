---
title: "Smart Webcam works on 10.04"
date: 2010-07-31
forum: General Help
---

### Post by ubuntu1sttimer on 2010-07-31
From time to time I have seen messages asking if their new device works on Ubuntu. This is to advise that I recently purchased a "Smart Webcam" brand inexpensive webcam at a local U.S. building products chain. Strange place to find such a thing but it was very low priced so I thought "why not give it a try". 

As it turned out, it works with my 10.04 install.  Shows up ok on Ekiga and in gstreamer-properties in terminal. The video image quality is not as good as some but is suitable for casual use.

The microphone is brought out via a "Y" off the USB cable and ends in a 1/8" audio plug that will plug into a sound input port. I have not tried the mic but it should work. There is almost no documentation provided. 

Lastly, I have no connection with either the manufacture or the store. Just thought someone might be considering one of these and wondering it would work  in Ubuntu. It does for me.

---

### Post by NFblaze on 2010-07-31
Cool if you can get the model information and such you can post the info and your review to a hardware compabitibility list such as the ones at [http://www.ubuntuhcl.org](http://www.ubuntuhcl.org) as inevitably your post will be sunk into the hidden masses.

---

### Post by ubuntu1sttimer on 2010-08-01
That is a "bit" of a problem as thy don't give a model number. In fact, the only description given is a banner across the top of the package that says "Smart Webcam". They have an item number of 85491 on the packaging but there is no printing of any sort on the camera. The only thing that comes with it is a three inch CD disk marked "Installation Disk". Since the label only mentions Windows I expect the disk is Window's drivers. No drivers appear to be needed with Ubuntu 10.04. 

The packaging does say that it is "3.0 Mega Pixels -- 3 Strong white LED -- 800x600 -- Build-in Microphone -- High-Speed USB 2.0". The LEDs don't work with Ubuntu. As mentioned in my first post, the 800x600 may be not be all that much as the image is usable but not as good am my other webcam. And, I have not tried to use the microphone.

At a price of under $8 U.S. you can't expect much. The chain store had some a few weeks ago. That is when I purchased mine. Now they have it in a a insert advertisement good through August 8, 2010. Based on past store actions, They will not keep something like this around too long after the sale ends.

---

### Post by NFblaze on 2010-08-01
What does 
```
ls /dev/v4l/by-id/
```

output when you plug it in?

Also try ```
dmesg | tail
``` after plugging it in

---

### Post by ubuntu1sttimer on 2010-08-01
Results as follows:

ls /dev/v4l/by-id/ 
usb-ARKMICRO_USB2.0_PC_CAMERA-video-index0

dmesg | tail
[   31.672009] eth0: no IPv6 routers present
[  314.384856] padlock: VIA PadLock not detected.
[  548.420033] usb 1-2: new high speed USB device using ehci_hcd and address 2
[  548.554771] usb 1-2: configuration #1 chosen from 1 choice
[  548.608333] Linux video capture interface: v2.00
[  548.616672] uvcvideo: Found UVC 1.00 device USB2.0 PC CAMERA (18ec:3290)
[  548.618422] uvcvideo: UVC non compliance - GET_DEF(PROBE) not supported. Enabling workaround.
[  548.619071] input: USB2.0 PC CAMERA as /devices/pci0000:00/0000:00:10.4/usb1/1-2/1-2:1.0/input/input5
[  548.619314] usbcore: registered new interface driver uvcvideo
[  548.621567] USB Video Class driver (v0.1.0)


Not sure what all this means but expect you do. I am at the stage where I just fight liniux. Great operating system but can be frustrating when things go wrong.

If I can help more, let me know.

---

### Post by ubuntu1sttimer on 2010-08-01
Left out one thing. For the first time I now have the three LEDs lite on the camera.

---

### Post by NFblaze on 2010-08-01
The webcam seems to have come from company Ark Micro. 
It's seems to be a generic chinese made webcam which is why it isnt particularly branded. It works tho! Glad we figured that out.

---

