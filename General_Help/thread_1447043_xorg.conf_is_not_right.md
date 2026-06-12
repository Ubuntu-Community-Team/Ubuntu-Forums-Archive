---
title: "xorg.conf is not right?"
date: 2010-04-04
forum: General Help
---

### Post by clutch| on 2010-04-04
Having the hardest time turning the mouse sensitivity down in xfce.  various xset settings make no real difference.  I move the mouse under an inch and it covers the entire screen easily.  razertool-gtk won't recognize my mouse (also, I couldn't find any documentation at all for it, but maybe I'm just dumb), the xfce settings don't lower it enough, and the last thing I was going to try was to edit my xorg.conf.  I though there was supposed to be a mouse section there, and this is all I have in my xorg.conf file:


```
Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
    Disable    "dri2"
EndSection

Section "Device"
    Identifier    "Default Device"
    Option    "NoLogo"    "True"
    Driver    "nvidia"
EndSection
```

---

### Post by wojox on 2010-04-04
You can run:

```
sudo nvidia-xconfig
```

to get a fuller more robust xorg.conf. ;)

---

### Post by clutch| on 2010-04-04
Ah, thank you.  I thought it had something to do with the nvidia stuff.  Its a new machine and I haven't ever had a nice video card like this one in the past.

Now I just have to sort out the sensitivity issue.  Its ridiculous, have been trying to get it lower for days with no success.  Attempting to lower the DPI is my last resort.  Hopefully it works.

/edit

```
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
```

Am I even looking in the right file?  lol.  I thought there was something in here for sensitivity/dpi settings, but it is not immediately apparent what to mess with.  ZAxisMapping doesn't seem to do anything.

I have no idea how to fix this.  My mouse is ultra-sensitive.  I've got the acceleration down to a manageable level, but the general sensitivity is still way too high.  Been Googling around for the last hour-ish with no working solutions.

How does xfce mouse settings not have a slider for Sensitivity?  That seems crazy.

---

### Post by clutch| on 2010-04-04
[http://ubuntuforums.org/showthread.php?t=1124557&highlight=mouse+sensitivity+DPI](http://ubuntuforums.org/showthread.php?t=1124557&highlight=mouse+sensitivity+DPI)

Tried the fixes in that thread.  No dice.

---

### Post by wojox on 2010-04-05
Try adding this option to it and mess around with the number to adjust it:

```
Option      "Sensitivity"       "0.24"
```

---

### Post by clutch| on 2010-04-05
Lol, I made about 9000 changes to various files and added a poopload of options to that section of xorg.conf last night.  Eventually gave up and shut it down.  Came back this morning and my mouse sensitivity was NUTS.  Like, acceleration was inverted.  Moving slow  caused it to accelerate wildly while a quick flick did almost nothing.  Anyway, xset m 1/3 0 actually does something now and it has become very manageable.  So it works, but still you would think that the devs would have made this process a little less painful by now.  Oh well. 

tl;dr

For anyone else who has this problem, play with the solutions mentioned in the thread I linked earlier and REBOOT between each change until you figure out what works for you.

I always do something stupid like that.  I never remember to try rebooting after I mess with something.  I just added a post-it to the edge of my monitor that says, "Reboot, dumbass."  Hopefully that will serve to remind me next time I have an issue.

:)

/edit Commented out the "ConstantDeceleration" option that I had added to xorg and it seems to have gotten rid of the last remnants of the inverted acceleration.  It feels like its still doing it a little bit, but its at least usable now.  I'll mess with everything else later and try to come up with a final, working, simple solution to anyone else who runs into this problem in the future.

---

