---
title: "Webcam works with Cheese but not with Skype"
date: 2010-10-15
forum: General Help
---

### Post by cocokessler on 2010-10-15
My webcam works with **Cheese** but not with **Skype.** 

I am running Maverick 10.10, kernel 2.6.35-22 **(32 bit)** on an HP DV2000 with Skype version 2.1.0.81
The webcam is detected by [FONT=”Courier New”]lsusb[/FONT] as [FONT=”Courier New”]Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera[/FONT]

I have tried some of the normal fixes found on many other threads (and [HERE]("https://help.ubuntu.com/community/Webcam")), including running the following commands from the terminal:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```
```
LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
```
```
export XLIB_SKIP_ARGB_VISUALS=1
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype'
```
I am able to launch Skype from the terminal, but Skype does not display video under options/"test" (I also tried it once during a real call, and it refused to display anything).  Cheese will properly take pictures and record video.

Any help or suggestions you are able to provide would be greatly appreciated.  

Thanks,
coco

---

### Post by Cpierce on 2010-10-15
This is what solved my issue, hopes it works for you

[http://ubuntuforums.org/showthread.php?t=1546777](http://ubuntuforums.org/showthread.php?t=1546777)

---

### Post by cocokessler on 2010-10-15
Cpierce, 

Thank you for your quick response!  Skype launches using the menu command:

```
sh -c 'export XLIB_SKIP_ARGB_VISUALS=1 && LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype'
```

But the video still does not work.  I tried the video in options/"test", and in a real call.

---

### Post by Cpierce on 2010-10-16
Sorry it didn't work. 10.10 must be different than 10.04. But it was worth a try.

---

### Post by cocokessler on 2010-10-18
bump

---

### Post by jesuisbenjamin on 2010-10-21
Same problem here: no solution from me i'm afraid. :s

---

### Post by jappie on 2010-11-07
I finally solved my webcam problem!! I tried before all the stuff below and my video would only work with Skype in "test mode". I solved this by running (alt-f2) the "gstreamer-properties", go to "video" and under "default input", "device" change to "usb webcam".

Good luck!
Jappie

---

### Post by cocokessler on 2010-11-08
Jappie,

Thank you for your answer.  Unfortunately, it did not work for me.

:(

---

### Post by mastablasta on 2010-11-08
which devices are showing in gstreamer-properties ?
 
because you might have to tell the computer to use the propper device. it might be recognising another device as camera. you could also change libv version there.

---

### Post by jappie on 2010-11-09
Cocokesler, Did you edit your skype start-up by: right click "applications", "edit menus", select "internet", "Skype"go to it's properties and fill in the following under "command":

bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'

Pura Vida!
Jappie

---

