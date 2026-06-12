---
title: "Out of range after installing drivers for ATI Radeon 5450 HD card"
date: 2011-06-26
forum: General Help
---

### Post by startgame412 on 2011-06-26
Hello, after installing the proprietary drivers for my ATI Radeon 5450 graphics card, I get and out of range message when trying to boot after the drivers are installed and am told to restart for the drivers to take effect. I believe I am having this problem because I am using an actual tv that dubs as a pc monitor. It is an AOC 22 inch LCD TV that is hooked up via VGA to my computer. I think I have to specify vertical and horizontal refresh rates as well as what resolutions it supports. The refresh rate is between 50 and 75 Hz and 30 to 80 khz. The resolutions supported are 1920 x 1080 @ 60 Hz
1680 x 1050 @ 60 Hz
1440 x 900 @ 60 Hz
1280 x 1024 @ 60 Hz
1280 x 768 @ 60 Hz
1024 x 768 @ 60, 75 Hz
800 x 600 @ 60, 75 Hz
640 x 480 @ 60, 75 Hz

What I think is going on is that ubuntu is trying to load at 1600x1200 which is a resolution my monitor does not support. How do I fix this? Thanks.

---

### Post by startgame412 on 2011-06-27
Anyone know what could the problem be and how to fix it? Thanks.

---

### Post by Wim Sturkenboom on 2011-06-27
You're  a bit impatient ;) Do a search for VertRefresh or HorizSync on this forum and you will find samples of the xorg configuration.

e.g. post 4 in [http://ubuntuforums.org/showthread.php?t=1725320&highlight=vertrefresh](http://ubuntuforums.org/showthread.php?t=1725320&highlight=vertrefresh)

Do not literally copy it but check how you can set the above parameters to limit what the video card will do.

---

### Post by startgame412 on 2011-06-27
Hi, I have just about solved my issue. The only thing is that now I have a 1 on the top left corner of my monitor. How do I remove this? Thanks.

---

### Post by startgame412 on 2011-06-27
Thanks for you help. I have solved this issue. The problem was since I am using a TV/PC monitor combo, resolutions higher than 1024x768 were not being picked up. Installing the proprietary drivers for my ati card for some reason makes the computer try to load at 1600x1200 for some reason and that resolution is not supported by my TV/PC monitor. I had to use xrandr and cvt to add missing resolutions and then had to add put the information into xorg.con. Thanks.

---

