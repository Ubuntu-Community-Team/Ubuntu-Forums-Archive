---
title: "No sound with newly installed 12.04"
date: 2012-09-13
forum: General Help
---

### Post by O-pos on 2012-09-13
Hello,

I just bought HP EliteBook 8460w, and installed Ubuntu 12.04. Everything works just fine, but no sound. Nothing has sound - youtube, movie files, music... Any thoughts?

---

### Post by ranger1021994 on 2012-09-13
Check this out
[http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/](http://www.unixmen.com/2012003-howto-resolve-nosound-problem-on-ubuntu/)
And this :
[http://ubuntuforums.org/showthread.php?t=1744966](http://ubuntuforums.org/showthread.php?t=1744966)

---

### Post by O-pos on 2012-09-13
Thanks! That helped to solve the problem with the laptop, however the sound is not transmitted through displayport/HDMI adapter. Only video signal gets transmitted. Switching the device for sound output from built-in audio analog stereo to "Caicos HDMI Audio [Radeon HD 6400 Series] Digital Stereo (HDMI)" does not help :(

---

### Post by ranger1021994 on 2012-09-14
Try reconnecting HDMI and switch to hdmi again....or try restarting..

---

### Post by O-pos on 2012-09-14
I realize now what the problem is: If I use the default open source driver, then there is no sound. If I use fglrx (proprietary driver), then both video and sound get through, however but there is a significant video tearing. How come there is no solution to that? Any advices?

---

### Post by ranger1021994 on 2012-09-14
Open Catalyst control centre from application list and then configure your graphic card so as to reduce video tear.

---

