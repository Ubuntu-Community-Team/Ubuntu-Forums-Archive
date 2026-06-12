---
title: "&quot;third button&quot; scroll emulation for touchpad"
date: 2006-05-31
forum: General Help
---

### Post by M4LFUNCT10N on 2006-05-31
I've been looking around, and it seems that all the posts asking how to scroll with a touchpad are asking how to use the side of the touchpad for scrolling.  That has always bugged me personally, as I've preferred the other method I have with my Toshiba(Satellite 1415-s174).  On my laptop, if I press both the left and right touchpad buttons at the same time, my touchpad is set in scroll mode.  Now, I just move my finger around on the touchpad to scroll up/down/left/right.

As I'm a noob, I'm sure this has been covered, however, I've searched quite a bit with no results.

---

### Post by conro on 2006-05-31
look in the file /etc/X11/xorg.conf for the section that defines your mouse.. mine looks like:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

```

notice the last option.. ZAxisMapping.. on my laptop it allows me to scroll by sliding my finger up and down on the side of the touchpad. 

try adding it to your xorg.conf file and restart xorg and it should work.

---

### Post by M4LFUNCT10N on 2006-05-31
[QUOTE=conro]look in the file /etc/X11/xorg.conf for the section that defines your mouse.. mine looks like:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection

```

notice the last option.. ZAxisMapping.. on my laptop it allows me to scroll by sliding my finger up and down on the side of the touchpad. 

try adding it to your xorg.conf file and restart xorg and it should work.[/QUOTE]

Okay... so that halfway solves the scroll... but is there a way to do the emulation?  A way to make the *whole* touchpad scroll once both buttons are pressed simultaneously.

***EDIT***

That is exactly what my xorg.conf has in it.  So... doesn't work for me.

---

