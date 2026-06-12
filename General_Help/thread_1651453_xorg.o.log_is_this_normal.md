---
title: "xorg.o.log is this normal"
date: 2010-12-23
forum: General Help
---

### Post by ubugaru on 2010-12-23
upon boot EDID repeatedly prints modelines

[    14.029] (II) intel(0): EDID vendor "AUO", prod id 4128
[    14.232] (II) intel(0): Printing DDC gathered Modelines:
[    14.232] (II) intel(0): Modeline "1024x600"x0.0   50.40  1024 1048 1184 1344  600 600 619 625 -hsync -vsync (37.5 kHz)
[    14.269] (II) intel(0): EDID vendor "AUO", prod id 4128
[    14.269] (II) intel(0): Printing DDC gathered Modelines:
[    14.269] (II) intel(0): Modeline "1024x600"x0.0   50.40  1024 1048 1184 1344  600 600 619 625 -hsync -vsync (37.5 kHz)
[    14.305] (II) intel(0): EDID vendor "AUO", prod id 4128
[    14.305] (II) intel(0): Printing DDC gathered Modelines:
[    14.305] (II) intel(0): Modeline "1024x600"x0.0   50.40  1024 1048 1184 1344  600 600 619 625 -hsync -vsync (37.5 kHz)
[    14.341] (II) intel(0): EDID vendor "AUO", prod id 4128
[    14.341] (II) intel(0): Printing DDC gathered Modelines:
[    14.341] (II) intel(0): Modeline "1024x600"x0.0   50.40  1024 1048 1184 1344  600 600 619 625 -hsync -vsync (37.5 kHz)
[    18.777] (II) intel(0): EDID vendor "AUO", prod id 4128
[    18.777] (II) intel(0): Printing DDC gathered Modelines:
[    18.777] (II) intel(0): Modeline "1024x600"x0.0   50.40  1024 1048 1184 1344  600 600 619 625 -hsync -vsync (37.5 kHz)
[    22.265] (II) intel(0): EDID vendor "AUO", prod id 4128
[    22.265] (II) intel(0): Printing DDC gathered Modelines:
[    22.265] (II) intel(0): Modeline "1024x600"x0.0   50.40  1024 1048 1184 1344  600 600 619 625 -hsync -vsync (37.5 kHz)

these are the final entries in the log, i am running maverick on an eeepc 901

---

### Post by ubugaru on 2010-12-27
seasons gruntings! 


does anybody else out there have similar repeated entries within their log file???

At least one would be able to submit an error report, what what!

;)

---

### Post by ubugaru on 2010-12-27
#!

---

### Post by vilain_mamuth on 2011-01-26
yes, me

```
[   256.355] (II) intel(0): EDID vendor "HWP", prod id 10330
[   256.355] (II) intel(0): Using hsync ranges from config file
[   256.355] (II) intel(0): Using vrefresh ranges from config file
[   256.355] (II) intel(0): Printing DDC gathered Modelines:
[   256.355] (II) intel(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz)
[   256.355] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[   256.355] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[   256.355] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[   256.355] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[   256.355] (II) intel(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz)
[   256.355] (II) intel(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz)
[   256.355] (II) intel(0): Modeline "1280x800"x0.0   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync (49.7 kHz)
```

repeated more than 300 times.

when i login to gnome, the screen flickers a lot of time. don't know if this is related

---

### Post by drevicko on 2012-12-02
An old old post, but I don't see any solutions here...

I'm having a similar problem in Ubuntu 12.04:

```
[    17.700] (II) RADEON(0): EDID vendor "SAM", prod id 694
[    17.700] (II) RADEON(0): Using EDID range info for horizontal sync
[    17.700] (II) RADEON(0): Using EDID range info for vertical refresh
[    17.700] (II) RADEON(0): Printing DDC gathered Modelines:
...
[    18.749] (II) RADEON(0): EDID vendor "SAM", prod id 694
[    18.749] (II) RADEON(0): Using hsync ranges from config file
[    18.749] (II) RADEON(0): Using vrefresh ranges from config file
[    18.749] (II) RADEON(0): Printing DDC gathered Modelines:
...
[    30.776] (II) RADEON(0): EDID vendor "SAM", prod id 694
[    30.776] (II) RADEON(0): Using hsync ranges from config file
[    30.776] (II) RADEON(0): Using vrefresh ranges from config file
[    30.776] (II) RADEON(0): Printing DDC gathered Modelines:
...
[    32.932] (II) RADEON(0): EDID vendor "SAM", prod id 694
[    32.932] (II) RADEON(0): Using hsync ranges from config file
[    32.932] (II) RADEON(0): Using vrefresh ranges from config file
[    32.932] (II) RADEON(0): Printing DDC gathered Modelines:
...
[    54.316] (II) RADEON(0): EDID vendor "SAM", prod id 694
[    54.316] (II) RADEON(0): Using hsync ranges from config file
[    54.316] (II) RADEON(0): Using vrefresh ranges from config file
[    54.316] (II) RADEON(0): Printing DDC gathered Modelines:
...
```


Not so bad as vilain_mamuth's 300 times, but annoying enough. As you can see it's taking around 40secs to log in...

---

