---
title: "Best working Webcam?"
date: 2010-04-21
forum: General Help
---

### Post by Lucky75 on 2010-04-21
Hi,

I'm looking to buy a new webcam to use under karmic/lucid, but I'm not sure which one is best. I've taken a look at the list of supported web cameras, but I was hoping for some recommendations. The cheaper the better :)

Thanks!

---

### Post by Lucky75 on 2010-04-22
bump

---

### Post by Lucky75 on 2010-04-23
bump

---

### Post by 3rdalbum on 2010-04-23
The only one I can suggest is available at [www.dse.com.au](www.dse.com.au) - it's **** Smith's own notebook webcam, it uses UVC so it works on all operating systems. I don't have time to find the actual page for you unfortunately, but you should be able to find it on there.

---

### Post by Lucky75 on 2010-04-24
Which one on there would you recommend?

I was hoping for one which had a built in mic and worked via usb.

---

### Post by Lucky75 on 2010-04-24
Bump

---

### Post by no2498 on 2010-04-24
if you have a old 1 plug it in
or if you get a new 1
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
click the bottom test button for each 1
904 and up cheese is loaded try it in cheese

---

### Post by Directive 4 on 2010-04-24
logictec

logic 3 with built in mic


maybe not best, but cheap, and it works

---

### Post by roasttoe on 2010-04-24
My Logitech QuickCam Messenger (with built-in mic) worked right out the box with Karmic, including Skype.

Needed slight tweaking with Lucid to get working in Skype however. The menu needed to be modified to launch Skype using the following params:

```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'
```

To do this, go to System -> Preferences -> Main Menu and find the Skype entry under the Internet menu.

Hope this helps.

P.

---

### Post by dominiquec on 2010-04-24
[My A4Tech works fine]("http://ubuntuliving.blogspot.com/2009/05/a4tech-webcam.html").  In principle, any of the driverless webcams should work with Linux.

---

### Post by bhaverkamp on 2010-04-24
I just bought a new logitech webcam and it works great too. Just make sure to look UVC support and it will just work. The box for mine also mentioned it supported linux.

---

### Post by Lucky75 on 2010-04-27
Thanks guys!

So, anything that supports UVC should work properly on linux? I was under the impression that a lot of them still didn't quite work properly.

---

### Post by Linuxforall on 2010-04-27
Logitech is the safest bet, Microdia chipset cams work but color is not that hot.

---

