---
title: "How do you reset resolution from terminal"
date: 2010-08-11
forum: General Help
---

### Post by dogwalker 2182 on 2010-08-11
Well, I've done it again.  This time I redefined the resolution on my monitor to 640x480 and in the middle of the reset, the definition routine shut down for no known reason.  This left the screen in an ambiguous state with much of the display off the screen at the bottom.  I reran the resolution routine and the "OK" button is off the screen to the bottom and I can't get to it to reset the resolution.  Nothing I can do raises the display up high enough to reach that button.  Put another monitor on the machine and it behaves fine at the correct resolution.  The question I have is:  Where is the definition file that I can delete for the other monitor so when I put the monitor back on line the parameters will be reread.  Thought it would be xorg-conf but it turns out that Xserver apparently takes care of it with something called EDID????  HELP.... By the way, this is 8.10, a very stable release.

---

### Post by sisco311 on 2010-08-12
You can hold down the ALT key and LEFT-click anywhere inside a window to drag it to a new location.

If you want to change the resolution from the terminal, then run:
```
xrandr
```to get a list of existing modes. The output should look like this:
```

 Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
**VGA-1** connected 1024x768+0+0 (normal left inverted right x axis y axis) 306mm x 230mm
   1024x768       85.0*+   75.1     75.0     70.1     60.0     43.5  
   1792x1344      60.0  
   1920x1200      59.9  
   1600x1200      75.0     70.0     65.0     60.0  
   1680x1050      74.9     60.0  
   1400x1050      85.0     74.9     60.0  
   1280x1024      85.0     75.0     60.0  
   1440x900       84.8     75.0     59.9  
   1280x960       85.0     60.0  
   1360x768       60.0  
   1280x800       84.9     74.9     59.8  
   1152x864       75.0  
   1280x768       84.8     74.9     59.9  
   800x600        85.1     72.2     75.0     60.3     56.2  
   848x480        60.0  
   640x480        85.0     75.0     72.8     60.0     59.9  
   720x400        85.0     70.1  
   640x400        85.1  
   640x350        85.1  

```

then change the resolution:
```
xrandr --output **VGA-1** --mode 1024x768
```

---

### Post by dogwalker 2182 on 2010-08-14
CISCO311:

Many thanks.  Never would have suspected it was that easy.  Used both methods to get educated.  Thanks again
DOGWALKER 2182:D

---

### Post by sisco311 on 2010-08-14
You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.

---

