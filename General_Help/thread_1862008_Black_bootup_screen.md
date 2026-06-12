---
title: "Black bootup screen"
date: 2011-10-16
forum: General Help
---

### Post by rmcnamara on 2011-10-16
I'm trying to figure out what this screen is that im getting on bootup. It is happening a lot. 

The screen comes up in the bootup process. When the purple ubuntu screen disappears and the desktop appears i get a black screen. The screen has a few lines of text on of them is checking battery state. And on the other side of the screen is "ok". I then have to restart a few times for the desktop to come up. It is extremely annoying. I am using 11.10

Thanks
Rob

---

### Post by Atamisk on 2011-10-16
THat's usually the screen that's on that Virtual Terminal shortly before X (the graphical display) starts up. Usually, if you wait, your login screen will come up. it can take up to a minute or two in some cases, so give it a minute before resetting your computer. 

Does it lock up at that screen?

---

### Post by rmcnamara on 2011-10-16
Im not sure if it is locking up at that screen. I havent let it sit there longer than a minute or so. 

Would it have anything to do with the ati video driver. I have not installed any other driver besides the one that came with the initial install. There has been many problems that i ahve read about with installing ati drivers with 11.10. So I have been reluctant to install anything else.

Rob

---

### Post by Atamisk on 2011-10-16
It could be that the driver is doing something odd. what is the last few lines of /var/log/Xorg.0.log ?

---

### Post by rmcnamara on 2011-10-16
These are the lines i just took from the log file.

896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  4038.355] (II) RADEON(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  4038.355] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  4038.355] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[  4038.355] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz)
[  4038.355] (II) RADEON(0): Modeline "1920x1080"x60.0  172.80  1920 2040 2248 2576  1080 1081 1084 1118 -hsync +vsync (67.1 kHz)
[  4038.355] (II) RADEON(0): Modeline "1440x900"x0.0   88.75  1440 1488 1520 1600  900 903 909 926 +hsync -vsync (55.5 kHz)
[  4038.355] (II) RADEON(0): Modeline "1600x1200"x0.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz)
[  4038.355] (II) RADEON(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[  4038.355] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)

---

### Post by Atamisk on 2011-10-16
Nothing looks out of the ordinary in that bit, but that's a bunch of not-so-useful information... are there any obvious errors in the file? 

sidenote, which ati driver are your running? Radeon or the proprietary fglrx?

---

### Post by rmcnamara on 2011-10-16
The proprietary one. It is the second one on the list. The first one which is the post release version does not install at all. I have read in other places that a lot of people are not able to install that one either.

---

### Post by 98cwitr on 2011-10-16
I just went through all of this an hour ago, see this thread:

[http://ubuntuforums.org/showthread.php?t=1859820](http://ubuntuforums.org/showthread.php?t=1859820)

---

### Post by Atamisk on 2011-10-17
Re-installing fglrx might prove useful, but i'd still like to see the Xorg and dmesg logs when this happens... if it's not too much trouble, could you put them in a pastebin? Just make sure no personal data is in them (there almost never is)

---

