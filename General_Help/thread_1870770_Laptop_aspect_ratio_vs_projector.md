---
title: "Laptop aspect ratio vs projector"
date: 2011-10-27
forum: General Help
---

### Post by dewdrop_world on 2011-10-27
Did a bit of searching around here, but didn't find the answer to my question.

My laptop has the (blasted) Intel integrated video, 1366x768 resolution. In a couple of days, I will need to connect to a projector and I'm assuming 1024x768 resolution. When I've done this before, X automatically switches to the projector's resolution (good) and the display is mirrored (good), but the display on the laptop stretches to use all the screen space, so everything looks short and squat (not good).

I found this thread [1] for letter boxing, but it seems to be about fixing the ratio on the projector screen (not the built-in), plus it's about a year old and the instruction to "open up xorg.conf" has me a bit perplexed.

[1] [http://ubuntuforums.org/showthread.php?t=1618573](http://ubuntuforums.org/showthread.php?t=1618573)

```
$ locate xorg.conf
/usr/lib/X11/xorg.conf.d
/usr/lib/X11/xorg.conf.d/05-evdev.conf
/usr/lib/X11/xorg.conf.d/10-synaptics.conf
/usr/lib/X11/xorg.conf.d/10-vmmouse.conf
/usr/lib/X11/xorg.conf.d/10-wacom.conf
/usr/share/man/man5/xorg.conf.5.gz
```None of the files in /usr/lib/X11/xorg.conf.d contains a Modeline, nor...

```
$ sudo grep -ri modeline /etc/X11
[sudo] password for dlm: 
Binary file /etc/X11/X matches
```So what's the real answer? I would really rather avoid doing "grep -ri 'modeline' /" for obvious reasons :)

Thanks.
James

---

### Post by SteveDee on 2011-10-28
> **dewdrop_world said:**
> ...So what's the real answer?...

...beats me! But here is another approach, which I've just tried. You really need a 2nd monitor to try this, if you can't get your hands on the projector.

 Connect 2nd monitor/projector
 Start or reboot computer
 In a terminal type:-
```

xrandr

```
...this should list display mode for your laptop (LVDS) and projector (VGA, or maybe VGA-0).

You can now reset the laptop display to 1366x768 (assuming this was a listed mode) from the terminal by typing:-
```

xrandr --output LVDS --mode 1366x768

```

...and change the projector:-
```

xrandr --output VGA-0 --mode 1024x768

```
...where "VGA-0" is whatever was returned when you first ran "xrandr"

I also recommend you type:-
```

man xrandr

```

...and go right to the end of this manual, and look at the examples.

---

### Post by dewdrop_world on 2011-11-08
Interesting. As it happens, though, the projector actually supported 1360x768, so I didn't have to endure much stretching after all.

I should probably play around with xrandr sometime, in case I'm in a similar situation in the future, but no time at the moment :(

Thanks!
James

---

