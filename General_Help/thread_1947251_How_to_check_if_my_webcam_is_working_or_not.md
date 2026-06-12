---
title: "How to check if my webcam is working or not?"
date: 2012-03-26
forum: General Help
---

### Post by annnowik on 2012-03-26
Hi Everyone!

How can I check if my plugged in usb webcam is working or not? My webcam has bult in led lights, which are lighting when I run an application using cam, but only when is dark (leds are turning on automatically). But how about day? Surely I mean how to check in my system if any application is using webcam or just webcam is beeing used? I use Ubuntu 10 and my webcam is seen as /dev/video1.
I know that some webcams has a little led informing about camera's working, but my has not.

I noticed, that when my cam is plugged but there's no application working which uses the cam, the cam is not active, as if it had no power (although it's plugged to usb) Is it possible?

---

### Post by Azdour on 2012-03-26
Hi,

You may want to install an application like luvcview. Normally from a terminal I would run:

```
sudo apt-get install luvcview
```

You could also install cheese:

[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

With my logitech web cam the power light does not come on until luvcview or another application like Skype uses it.

---

### Post by pqwoerituytrueiwoq on 2012-03-26
you can always install [cheese]("apt:cheese") and see if it works 
if you want to see if your camera is active there is a app called [camera monitor]("apt:cameramonitor") you can use it will let you know when it is looking at you

---

### Post by annnowik on 2012-03-26
Thanks guys!
Camera monitor is exactly what I'm looking for. Thank you pqwoerituytrueiwoq.

---

