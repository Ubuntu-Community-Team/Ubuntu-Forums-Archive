---
title: "Please help! Emergency!"
date: 2010-06-17
forum: General Help
---

### Post by VinoFuriaRoja on 2010-06-17
Hi guys, 

I need some help as fast as I can get it within the next 2 hours. 

I have a videomeeting set up to run in 2 hours, and I went out and bought a webcam to run on 10.04.  I searched the boards finding out what the best cam to buy, and the general consensus was a Logitech webcam.  

I purchased a Logitech HD Webcam C310 from Best Buy, and opened up and installed it.  I tried it on Skype, and I get nothing for video in the test options.  I can see that it says "UVC Camera (046d:081b) (/dev/video0) under VIDEO DEVICES from OPTIONS, and I click on the TEST button and nothing happens. I double click on it and I get a full gray screen.  

I tried it out on Cheese and I get nothing but a black screen, but I can see the light on the webcam, and even took a few pictures to test it out.  When I tried recording video, it started, but I could not stop it.  It froze on me and I had to do a force quit to get out of it.  When I ran the video playback, all I got was a black screen and a long beep noise.  

Finally, I ran lsusb and got the following:

mark@mark-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 046d:081b Logitech, Inc. 
Bus 001 Device 007: ID 05ac:1290 Apple, Inc. iPhone
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mark@mark-laptop:~$ 


and lsmod | grep videodev  revealed the following:

mark@mark-laptop:~$ lsmod | grep videodev
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
mark@mark-laptop:~$ 


Please guys, any help would be much appreciated as I have to get this up in running by 7pm!  Thanks again.  

Mark

---

### Post by VinoFuriaRoja on 2010-06-17
bump...please help me out guys

---

### Post by VinoFuriaRoja on 2010-06-17
bump

---

### Post by emarkay on 2010-06-17
Oh yea, webcams in Ubuntu - that's been a problem for ages - I gave up on it - but I did get a Logitech one (blue and white circular one (I think it was IM pro) or something to get images onscreen.

Let me research.

---

### Post by emarkay on 2010-06-17
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
[http://ubuntuforums.org/showthread.php?t=997807](http://ubuntuforums.org/showthread.php?t=997807)
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)

[http://www.quickcamteam.net/devices](http://www.quickcamteam.net/devices)
[http://linux.about.com/od/wcm_howto/a/hwtwcm03t02.htm](http://linux.about.com/od/wcm_howto/a/hwtwcm03t02.htm)
[http://ubuntuforums.org/showthread.php?t=50257](http://ubuntuforums.org/showthread.php?t=50257)
[http://superuser.com/questions/85500/webcam-problem-with-skype-on-linux](http://superuser.com/questions/85500/webcam-problem-with-skype-on-linux)

---

### Post by WorMzy on 2010-06-17
Mine works fine; lsusb:
```
Bus 008 Device 002: ID 046d:08ad Logitech, Inc. QuickCam Communicate STX
```

I've got the following modules loaded:
```
v4l1_compat            15546  1 videodev
v4l2_compat_ioctl32    10641  1 videodev
i2c_core               17959  4 adt7475,videodev,i2c_i801,nvidia
```

No idea which ones are being used, but try loading them all. You might need to download some other packages to get these modules, I'm not sure if you do or not, or which packages contain them.

---

### Post by VinoFuriaRoja on 2010-06-17
So it looks like my system is not recognizing or does not have the proper modules installed?

---

### Post by glococo on 2010-08-12
DId you try with the last kernel ? 2.6.35 ?

If you dont have any nVidia or Ati video binary driver, try the last kernel from the ppa repositories ->

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35-maverick/)

You should download and install in the following order:
linux-image-2.6.35-020635-generic_2.6.35-020635_i386.deb
linux-headers-2.6.35-020635-generic_2.6.35-020635_i386.deb
linux-headers-2.6.35-020635_2.6.35-020635_all.deb

Hope with the last kernel work.

K,Regards!

---

### Post by baddnady23 on 2010-10-30
Mine works great with simply plugging it in and going.

```
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
**Bus 001 Device 005: ID 046d:081b Logitech, Inc.** 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

You sure your USB port works?

---

### Post by cwwilson721 on 2010-10-30
I know these are simple, but sometimes, we all forget...

Did you reboot AFTER you plugged in the webcam? Sometimes needed. Not always, but doesn't hurt)

Have you tried uninstalling/reinstalling Skype? (You might have wrong one. the one from Skype.com works, but you're better off not using it. Make SURE it's installed thru Software center. That one has the wrapper for your webcam)

What does the Skype icon properties say in the 'command' box? (Has to be skype-wrapper. If it's NOT skype-wrapper, you have wrong skype installed)

---

