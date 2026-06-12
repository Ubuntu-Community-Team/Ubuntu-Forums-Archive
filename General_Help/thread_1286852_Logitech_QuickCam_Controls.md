---
title: "Logitech QuickCam Controls?"
date: 2009-10-09
forum: General Help
---

### Post by paradox_inversion on 2009-10-09
Hey all. First post in a while (I forgot I had an account here!).

At any rate, I recently resurrected my laptop from the dead with a new install of Ubuntu, and it runs better than the first day I got it... With a clean XP Pro install. The only issue standing out at the moment is my webcam. It's a Logitech Orbit (MP, I believe). The camera should be capable of panning and tilting, by way of GUI control, but I don't know how to get that to work. The only solution I've thought of (but haven't tried yet) is running the Logitech Installer through WINE, but I'd really rather avoid that, if at all possible. 

So, does anyone know if there's a program that will give me control of my webcam once again? I don't really care about the facial recognition and all that... Just want to be able to pan, tilt, and zoom. Thanks all! So far, Ubuntu ROCKS. This, by the way, is the second Ubuntu system I've had. Both saved the day when Windows decided to crap out. Says a lot!

---

### Post by paradox_inversion on 2009-10-11
Alright! It took me a lot of googling and stumbling through code, but I have found a solution. I eventually was taken to [http://www.quickcamteam.net/](http://www.quickcamteam.net/) . From there, I downloaded libwebcam. I also got [http://guvcview.berlios.de/](http://guvcview.berlios.de/) and downloaded guvcview. With these two programs, I now am able to pan, tilt, mess with all the color settings, as well as focus. Through guvcview, I can also capture pictures and video on my webcam, and most importantly, save setting profiles! [http://snipplr.com/view/19847/install-libwebcam-ubuntu-910/](http://snipplr.com/view/19847/install-libwebcam-ubuntu-910/) was the biggest help in installing this. Line by line code. (If only it helped me remember all that too ;P)

For those of you who don't know, I have a quickcam orbit mp. lsusb is as follows:
```
Bus 001 Device 009: ID 046d:08cc Logitech, Inc. Mic (PTZ)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 007: ID 04f3:0213 Elan Microelectronics Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Running Jaunty, 9.04. Good luck for anyone else with this question.

---

### Post by Neatoman on 2012-03-29
Hello paradox-

I see this is a 2 1/2 year old thread, but it seems the closest to what I need, so I'm hoping you're still around and can help me anyway.  

I am trying to get a QuickCam Orbit MP up and running on Ubuntu 11.10.   I have installed guvcview as you suggested here, but quickcamteam.net no longer exists.  I was able to find libwebcam in the Software Center - hopefully the same thing - and installed that as well.  Guvcview looks very nice but I do not see any PTZ controls in it.  Have I done something wrong?  What am I missing?

Thanks in advance.

---

### Post by howefield on 2012-03-29
Old thread closed.

Start a new one please.

---

