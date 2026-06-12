---
title: "Way to know if a laptop is using an external screen from a script?"
date: 2009-08-19
forum: General Help
---

### Post by tnek on 2009-08-19
Hi,

When I'm at home, I'm using an external screen with my laptop. And when I'm out on the run I naturally use the built in screen.

I would like to take certain actions in a script when I'm using an external screen. But I don't know how I could check if I'm using one or not. Any tips?

---

### Post by MaxIBoy on 2009-08-19
Are the screens in "big desktop mode" (I.E. can you drag windows between them?)

---

### Post by DaithiF on 2009-08-19
Hi,
assuming the screens have different resolutions(?) then you can test for the resolution using xwininfo.
xwininfo gives information about whatever window you select interactively, but you can also give it a window id, or for the overall display the -root parameter.
so:
height=$(xwininfo -root | grep "Height:" | cut -d':' -f2 )
width=$(xwininfo -root | grep "Width:" | cut -d':' -f2 )
echo $height $width

---

### Post by tnek on 2009-08-28
I think I've found a key command to having a better way. If I use xrandr I get this output:
```

$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 960, maximum 1680 x 1680
VGA connected 1280x960+0+0 (normal left inverted right x axis y axis) 464mm x 290mm
   1680x1050      60.0 +
   1600x1000      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0* 
   1152x864       75.0  
   1152x720       60.0  
   1024x768       75.0     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
   720x400        70.1  
LVDS connected (normal left inverted right x axis y axis)
   1280x800       59.9 +
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  

```

That's when I have plugged in and am using my external monitor. It looks like a step in the right direction, right? (I'll get back to the thread when/if I get something working.)

---

### Post by DaithiF on 2009-08-28
Hi,
what does it output when its just your laptop screen?  The key will be to find the piece of information that is different depending on the display, right?  If not current resolution, then maybe maximum, or were you thinking something different?

---

### Post by tnek on 2010-05-07
Sorry for answering so late, and waking up a dead thread. :-) But it doesn't output the VGA row and all the possible resolutions below it when the VGA isn't connected. I used a grep line and an if, then turned off the internal monitor if the external one is connected before GDM was loaded.

---

