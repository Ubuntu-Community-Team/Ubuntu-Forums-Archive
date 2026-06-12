---
title: "Display Problem - Nvidia @ 1360x768"
date: 2009-11-07
forum: General Help
---

### Post by sleepingsword on 2009-11-07
I have recently put together a PC I want to use as a Media Centre

Ubuntu 9.04
p4 560 (3.6ghz)
4gb pc6400 ram
Nvidia 9600gt
Toshiba Regza 32in LCD (32AV605PG)

I have hooked it to the analogue VGA connector and am using it at 1360x760 resolution.

All was well untill I installed the Nvidia (180) driver, now the screen is offset to the right by a couple of inches.

The screen controls on the TV only allow me to move it a little and I cant get it to move over enough to see the date/time and shutdown button.

The alignment is fine using the driver that instaled with the OS but for some reason the nvidia driver has messed it up.

Can anyone give me an idea how to fix this?

Thanks :)

---

### Post by sleepingsword on 2009-11-07
Oh I'm using 9.04 because XBMC isnt fully compatible with 9.1 yet.

---

### Post by sleepingsword on 2009-11-08
ha-do-bump!

---

### Post by realzippy on 2009-11-08
Open nvidia-settings...

---

### Post by sleepingsword on 2009-11-08
I have and I cant see anything in there to move the screen. I can change the resolution fine, but at 1360x768 its miss-aligned by alot...

---

### Post by P4man on 2009-11-08
Most LCDs have an "auto" button that should correct that. You are probably sending at a different refresh rate as with the standard nv drivers. If you have a very strange monitor that doesnt let you autocorrect the alignment, try using a different refreshrate

---

### Post by sleepingsword on 2009-11-08
yeah the auto does try to fix it, and I have tried manually but its still way off.

Only have 1 refreshrate to choose (60) 

Annoying thing is if I disable the Nvidia driver it fits OK, but then XBMC is all choppy

---

### Post by realzippy on 2009-11-08
Tried xvidtune?

[http://languor.us/adjusting-display-screen-position-using-xvidtune](http://languor.us/adjusting-display-screen-position-using-xvidtune)

---

### Post by sleepingsword on 2009-11-08
xvidtune looked perfect however it did not seem to work as I got an error: unable to query monitor info

Thanks to the link I think what I need to do is edit my xorg.conf file and add the hsync values.

I opened my xorg.conf file and it has very little info on it:
                                               

[INDENT][INDENT]Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection[/INDENT][/INDENT]

So I dont quite understand how to update my xorg.conf file to contain the correct information?

My exact TV spec accoording to the service manual is:

Format: WXGA
Resolution: 1360x768 
V Frequency: 60.015Hz
H Frequency: 47.712kHz
Pixel Clock: 85.500MHz

Thanks for the help so far, as you have guessed I am a begginner ;)

---

### Post by P4man on 2009-11-08
```
gksudo gedit /etc/X11/xorg.conf
```

try adding this red line

```


Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
[COLOR="DarkRed"]       Modeline "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync[/COLOR]

EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

if that doesnt help, try this line instead:
Modeline "1360x768R"   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync

---

### Post by sleepingsword on 2009-11-08
P4man, you nailed it, it fits even better than the default driver.

Many thanks to you good sir!

(was the red text that did it)

---

### Post by P4man on 2009-11-08
great :)

for reference what I did was create a modeline with the built-in gtf utility.
In a terminal type

```
gtf horizontal_res vertical_res refreshrate
```

and it will spit out that line. For instance.
```

bob3@bob3-desktop:~$** gtf 1360 768 60**

  # 1360x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 84.72 MHz
  Modeline "1360x768_60.00"  84.72  1360 1424 1568 1776  768 769 772 795  -HSync +Vsync

```

Im not entirely sure, but it seem you need gtf for tv's and for lcd's or crt monitors you need cvt, which works the same but gives somewhat different results:
```

bob3@bob3-desktop:~$** cvt 1360 768 60**
# 1360x768 59.80 Hz (CVT) hsync: 47.72 kHz; pclk: 84.75 MHz
Modeline "1360x768_60.00"   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync
```

If you feel like testing the second option let me know if that works too or not, Id be interested in learning :)

---

