---
title: "Skype can't use webcam"
date: 2010-03-31
forum: General Help
---

### Post by MasterMIKE on 2010-03-31
Basically the webcam shows up in the list but clicking test does nothing, it just sits there. The webcam works perfectly in cheese.

I used too solve this problem by doing the following

type
 	Code:
> [FONT=monospace]sudo gedit /usr/local/bin/skype[/FONT][FONT=monospace]

[/FONT]and paste the following 2 line
 	Code:
> #!/bin/bash
michael@michael-desktop:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so /usr/bin/skype

then make it executable
> sudo chmod a+x /usr/local/bin/skype

But this doesn't seem too work now, not since I reinstalled ubuntu.

NOTE: I am using the 64bit release.

---

### Post by khelben1979 on 2010-04-09
Maybe the driver for the webcam don't work well because you're on a 64 bit system? I think it can be the source of the problem.

Have you ever considered getting another webcam?

---

### Post by tubbygweilo on 2010-04-09
MasterMIKE, I came across this list of video / web cameras that should work under Linux, I'm not sure if they work under Ubuntu but the list may be well worth a browse and a bit of research.

The Linux [UVC]("http://linux-uvc.berlios.de/") project

---

### Post by no2498 on 2010-04-09
im not trying to pick on cheese ubuntu give it all the webcam settings

but it breaks my cam can not use it in any other program after i open cheese
to reset the cam
open a terminal type, gstreamer-properties click enter
click video try v4l1 and v4l2
use the best pic click close

wxcam works for me to record video's and take pics with
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

comes in a deb file too

hope this helps

---

### Post by MasterMIKE on 2010-05-23
Sorry for the late reply. Haven't been on the forums in a while. In the end I just gave up and bought a new one. The Logitech one supported by ubuntu. Works like a charm ;)

---

### Post by khelben1979 on 2010-05-23
> **MasterMIKE said:**
> Sorry for the late reply. Haven't been on the forums in a while. In the end I just gave up and bought a new one. The Logitech one supported by ubuntu. Works like a charm ;)

I'm curious on what Logitech model you chose.

---

### Post by MasterMIKE on 2010-05-23
I bought the Logitech Webcam C200. Works out of the box on win7 and ubuntu 64bit. I just plugged it in and it worked ;)

---

### Post by no2498 on 2010-05-23
50 50 chance unplug the new 1 and plug in the old 1 it works now

---

### Post by MasterMIKE on 2010-05-23
lol as much as I'd love that to have worked it didn't lol. Besides i'm happy with my new webcam ;) Thanks anyway

---

