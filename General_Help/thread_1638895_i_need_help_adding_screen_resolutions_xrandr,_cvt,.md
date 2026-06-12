---
title: "i need help adding screen resolutions: xrandr, cvt, etc."
date: 2010-12-06
forum: General Help
---

### Post by branscombe_richmond on 2010-12-06
i need to have higher screen resolutions beyond 1024x768, like many ubuntu users. 

i have read up on how to add them, and it seems quite simple, but i dont know where things are going wrong.  i do know *what* is going on, just not *where*.





using the link here [ [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) ] i executed the following in order:

**execute XRANDR to display known screen/video resolution properties.**
```
death@death-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 300mm x 230mm
   1024x768       75.1     70.1     60.0*
   832x624        74.6 
   800x600        72.2     75.0     60.3     56.2 
   640x480        72.8     75.0     66.7     60.0 
   720x400        70.1 

```




**find the properties needed for a new screen resolution with the CVT command.**
in this case, i will add the output of the native 1024x768 as well as the output of a size i would like to add:
```
death@death-desktop:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync


death@death-desktop:~$ cvt 1152 768
# 1152x768 59.78 Hz (CVT) hsync: 47.71 kHz; pclk: 71.75 MHz
Modeline "1152x768_60.00"   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync

```






**create the undetected screen res. mode as follows.**
```
xrandr --newmode "1152x768_60.00"   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync


```






**finally _add_ the newly created mode to the list of resolutions.**
```
xrandr --addmode VGA1 1152x768_60.00


```


then i test the screen res.






now in the case of this BRAND NEW res., it works, but is overscanned  to the LEFT HAND SIDE of the screen.  if i try one of my other added res.'s, it goes out of range in terms of HORIZONTAL frequency.


something is not correct in my CVT values, but i don't know how to get the proper values.  can someone help me tweak this?



the 1152 screen res is showing as a 3:2 display, with a 59Hz refresh.


a complete output of my xrandr is as follows:
```

death@death-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 2048 x 2048
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 300mm x 230mm
   1024x768       75.1*    70.1     60.0 
   832x624        74.6 
   800x600        72.2     75.0     60.3     56.2 
   640x480        72.8     75.0     66.7     60.0 
   720x400        70.1 
   1200x1600_60.00   59.9 
   1280x1024_60.00   59.9 
   1152x768_60.00   59.2




```


i hope someone can help!


my MONITOR is a RADIUS KDS RAD-5.  i google it and find it has a "max" resolution of 1024x768 - **but!**  i'm certain an XP boot yielded higher resolutions!


ugh, i don't know - maybe i am stuck at 1024 until i can get a new monitor.  i hope not, but if so, please someone tell me if my provided specs make sense out of CVT and if it really is just my monitors limits.






now that i google about the monitor i feel kinda dumb, but who knows what the forum has to offer?  :/

---

### Post by dandnsmith on 2010-12-06
I cannot debug those lines - getting the timings right, and not breaking the display is something I haven't looked at for a long time, as automatic configuration has improved.

I did have a script to map things out, and sources for modelines, but they are out-of-date and the script invokes tools not now available.

To cut to the chase, what WinXP or other non-Ubuntu OS can do may be completely irrelevant, as they will use completely different drivers. The problem is likely that the driver module(s) you use with your hardware have limits - I have encountered this with several of my systems. One of the drivers I know is limited is the 'vesa' module - but a google search has given no detail on what the limits are.

I suggest you use the 'lsmod' command, check the modules to see which driver(s) you use, and then do your own hunt. I'm afraid you may have to work by eliminating non-applicable drivers from the list (I don't have a shortcut for this).

---

### Post by QLee on 2010-12-06
[QUOTE=branscombe_richmond]...
now that i google about the monitor i feel kinda dumb, but who knows what the forum has to offer?  :/[/QUOTE]
LCDs generally display best at their native resolution.

Your monitor has a 4:3 aspect ratio.

If you want to try other resolutions you should use ones with the 4:3 aspect ratio.

However, and it is a fairly big however, there is no guarantee you would be satisfied with the display at even a reasonable change outside of the native resolution. That is not an expensive nor high quality monitor in the beginning, it is a budget monitor. These days you'd probably be happier with a widescreen 16:9 monitor anyway, maybe the after Christmas sales could be a good time to pick one up. By the way, I'm typing this on a 1024x768 screen, it works for me.

---

### Post by branscombe_richmond on 2010-12-07
> **QLee said:**
> LCDs generally display best at their native resolution.

Your monitor has a 4:3 aspect ratio.

If you want to try other resolutions you should use ones with the 4:3 aspect ratio.

However, and it is a fairly big however, there is no guarantee you would be satisfied with the display at even a reasonable change outside of the native resolution. That is not an expensive nor high quality monitor in the beginning, it is a budget monitor. These days you'd probably be happier with a widescreen 16:9 monitor anyway, maybe the after Christmas sales could be a good time to pick one up. By the way, I'm typing this on a 1024x768 screen, it works for me.




aside from the monitor, i think it may come down to the chipset on my mobo.
i'm starting to look into the 915 chipset.  if anyone has any advice about it, please help.  thx!

---

### Post by branscombe_richmond on 2010-12-08
i'm starting to look into the 915 chipset.  if anyone has any advice about it, please help.  thx!

---

