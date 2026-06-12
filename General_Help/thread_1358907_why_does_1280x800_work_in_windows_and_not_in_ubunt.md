---
title: "why does 1280x800 work in windows and not in ubuntu?"
date: 2009-12-18
forum: General Help
---

### Post by mylo9000 on 2009-12-18
OK so I can't get a viable answer as to why I can't configure xorg to display at my tft's max res of 1280x800 or select any other refresh other than 60. 

the lcd is detected as a crt; aparently its because i'm using a vga cable. the monitor only has a vga port so i can't use anything else. 

on this same system if i install windows xp and install the nvidia drivers for my geforce 6200 i can max out my res at 1280x800@60 works great looks great.

this however is not possible in ubuntu. the only options i get are:

1360x768@60
1152x864@60
1024x768@60
and all the lower res's that hurt my eyes.

in prior versions of ubuntu i could set the refresh to 75 and i could get 1280x800 but it flickered like crazy would give you a head ache after 2 or 3 minutes.

its really bad that all my icons are ovals. whats worse is that this same setup works fine in windows.

why is this res so impossible to setup and why can windows set the res with ease?

I really want to use this screen to its full potential. if i can't i'll introduce the screen to mr. sledge hammer.  --yes i'm that frustrated--

sys spec:
amd athlon xp 64 3200+
2gb ram
nvidia geforce 6200
karmic
2.6.31-16-generic

---

### Post by unmole on 2009-12-18
Which graphic driver did you install in ubuntu?

---

### Post by mcse37 on 2009-12-19
My monitor was also incorrectly identified as a CRT instead of LCD.  You may have to 
manually edit your xorg.conf.  I've pasted the "Monitor" section of my file below.
You'll need to adjust the values to fit your monitor.  And of course, backup xorg.conf first:

Section "Monitor"
Identifier "Configured Monitor"
Vendorname "Generic LCD Display"
Modelname "LCD Panel 1280x1024"
Horizsync 30.0 - 83.0
Vertrefresh 55.0 - 75.0
modeline "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
modeline "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
modeline "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
modeline "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
modeline "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
modeline "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
Gamma 1.0
EndSection

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
Defaultdepth 24
SubSection "Display"
Depth 24
Virtual 1280 1024
Modes "1280x1024@60" "1280x960@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
EndSubSection
EndSection

---

