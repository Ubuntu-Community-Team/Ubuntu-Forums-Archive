---
title: "Maverick: xrandr --dpi fails to change resolution"
date: 2010-11-21
forum: General Help
---

### Post by ub40d on 2010-11-21
I need to set the resolution of my display to 96 dpi.

The command that used to work was
    $ xrandr --dpi 96

In Maverick, this gives me
    xrandr: Failed to get size of gamma for output default

and the resolution stays at the incorrect value, as proved by
    $ xdpyinfo | fgrep resolution

which outputs
    resolution:    104x105 dots per inch

The error message about gamma seems to be unrelated. I managed to shut it up with
    $ xrandr --output default --gamma 1:1:1 --dpi 96

which outputs...
    xrandr: Gamma size is 0.

...without error messages, but the resolution is still wrong:
    $ xdpyinfo | fgrep resolution
    resolution:    104x105 dots per inch

How can I reliably set my screen resolution to the desired dpi in Maverick? Needless to say, System / preferences / appearance / fonts / details / resolution is ALREADY set to 96 dpi, and this has no effect on the resolution seen by xdpyinfo (and, crucially, emacs-gtk).

Thank you

---

### Post by ub40d on 2010-11-21
Further discoveries:

1) xrandr acts upon the --dpi option regardless of the error message about gamma: I can see that by turning on the --verbose option.

$ sudo xrandr --verbose --dpi 100
xrandr: Failed to get size of gamma for output default
screen 0: 1600x1200 406x304 mm 100.00dpi

2) Unfortunately, what xrandr thinks it has done to the X server differs from what xdpyinfo (and emacs-gtk) think about it:

$ xdpyinfo | fgrep resolution
  resolution:    104x105 dots per inch

This happens in Maverick. I don't have that problem in Karmic, where if I set the dpi with xrandr to a given value, and then query it with xdpyinfo, the result is indeed the value I did set.
I don't have a Lucid machine to test whether the regression failure was introduced by Maverick or by Lucid.

---

### Post by ub40d on 2010-11-22
Further info: 
I tried this on another Maverick machine and there it all worked as expected:

 $ xdpyinfo | fgrep resolution
  resolution:    96x96 dots per inch

$ xrandr --dpi 100

$ xdpyinfo | fgrep resolution
  resolution:    100x100 dots per inch

$ xrandr --dpi 96

$ xdpyinfo | fgrep resolution
  resolution:    96x96 dots per inch

So, what could be the problem on the machine where it doesn't work? Different graphics driver? Any relevant configuration files I could post to help diagnose?

Thanks

---

### Post by AlanPorter on 2011-01-05
Same problem for me.

Dell XPS L501X, laptop.
NVIDIA GeForce GT 435M 2GB graphics

The 1920x1080 display is nice, but I would love to set the DPI a LOT higher so the text has large and crisp letters.

Alan Porter

---

