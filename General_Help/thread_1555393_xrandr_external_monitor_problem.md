---
title: "xrandr external monitor problem"
date: 2010-08-18
forum: General Help
---

### Post by tramir on 2010-08-18
I would really appreciate some help with the following problem. I have Lucid installed on an older Dell Inspiron 6000 (Ati X300 video card, no longer supported by fglrx, so using the open-source ati driver). I connected an LCD TV via VGA. The TV was detected and output is shown, but xrandr reports a resolution of 1360x768 while the TV reports a resolution of 1024x768. The outcome is that the image does not fill the whole screen (it's a bit shifted to the right, with a black stripe on the left). If I change the resolution to something less than 1024x768, both the TV and xrandr report the same correct resolution. I don't really know what to try to solve this and a 2-day search on ubuntu forums, launchpad and google did not yield anything useful. Does anybody have any idea? Thanks in advance...

---

### Post by realzippy on 2010-08-18
*Does anybody have any idea?*

Have you checked the LCD's menue?

    -------------------
Is LCD's native resolution 1360x768 ?

What does

```
xrandr -q
```

say when both monitors plugged in?

---

### Post by tramir on 2010-08-18
Yes, the LCD's native resolution is 1360x768 (when I connect another computer to it, it uses that resolution).

Here is the output of xrandr -q:

```
Screen 0: minimum 320 x 200, current 1360 x 768, maximum 4096 x 4096
VGA-0 connected 1360x768+0+0 (normal left inverted right x axis y axis) 1150mm x 650mm
   1360x768       60.0*+
   1280x720       60.0     60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        60.0  
   720x400        70.1  
LVDS connected (normal left inverted right x axis y axis)
   1280x800       60.4 +
   1360x768       59.8  
   1280x720       59.9  
   1152x768       59.8  
   1024x768       60.0     59.9  
   800x600        60.3     59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.9     59.4  
S-video disconnected (normal left inverted right x axis y axis)

```

So xrandr thinks it's sending output at 1360x768, but the TV gets it as 1024x768...

---

### Post by realzippy on 2010-08-18
..or the the TV converts it to 1024x768...

Have you checked the TV's menue?

---

### Post by tramir on 2010-08-18
I checked the TV menus and couldn't find anything of the sort. I connected another computer (granted, to the HDMI input) and it got a 1360x768 resolution without problems. So it seems to me it's not on the TV side, unless somehow it treats VGA and HDMI inputs different. Plus, the "conversion" to 1024x768 only happens for the 1360x768, all the other resolutions are recognized as such...

---

### Post by realzippy on 2010-08-18
No idea,someone else??

So you played with xrandr,e.g. the *newmode/addmode* stuff?
Created new modeline with *cvt* aso. ?

---

### Post by tramir on 2010-08-18
I did everything other than create a new modline. I'll try that too -- though xrandr already has a modline for the right resolution and it applies that. I'll try to find the specs of the TV and create a new modline. I'll report later tonight, when I get back home. Thanks.

---

### Post by realzippy on 2010-08-18
create one by cvt:

```
cvt 1360 768 60
```

and delete existing line before adding new one..

---

### Post by tramir on 2010-08-18
I feel so stupid... There was a hidden menu in the TV options that controlled the resolution and that was set at 1024x768... Once I found that, I was able to change the resolution and geometry and now everything works perfect. Sorry for all the trouble and thanks for all the help!

---

### Post by realzippy on 2010-08-19
...that's why I asked twice for TV menue;they can be real tricky...
Have fun!

---

