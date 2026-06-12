---
title: "change default maximized windows size"
date: 2011-07-30
forum: General Help
---

### Post by thombark on 2011-07-30
My laptop has a small flickering area at the bottom of the screen, about 1  cm high. It's a hardware problem. It's very annoying but I can just put a bit of dark paper over it. I would like to change the ubuntu (10.04) defaults so that the  bottom of the screen is never used - I can change some windows, but is there a global way to stop all windows, menus etc from using that lower area. Thanks.

---

### Post by realzippy on 2011-08-01
You should not double post a thread.Came across
[http://ubuntuforums.org/showthread.php?t=1816207](http://ubuntuforums.org/showthread.php?t=1816207)
minutes ago and remembered this one.
If you get no answer within 24 hours,you are allowed to
post a "bump" to your own thread so it comes up in the new posts.
Yesterday I did a short research about your problem with no
results.
Which laptop is it?
What does 
```
lspci |grep VGA
```
say?

---

### Post by realzippy on 2011-08-02
I have got a solution:

```
xrandr --fb 1366x668 --output LVDS1 --mode 1366x768 --panning 1366x668
```

does exactly what you want (on my machine):
cuts off the lower 100 pixels.
To make it work on your machine,you might have to edit
your resolution (mine is 1366x768 ) and your output name (mine is LVDS1).
Get yours with
```
xrandr -q
```
Also your driver has to support randr 1.3 off course...

---

### Post by thombark on 2011-08-03
[SIZE=2]Thank you - sorry if I broke the rules of the forum, I thought that the Desktop forum was more appropriate.

Here are the results:  lspci VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

xrandr --fb 1280x700 --output LVDS1 --mode 1280x800 --panning 1280x700  

xrandr: specified screen 1280x700 not large enough for output LVDS1 (1280x800+0+0) 

X Error of failed request:  BadMatch (invalid parameter attributes) 

Major opcode of failed request:  149 (RANDR)   Minor opcode of failed request:  29 (RRSetPanning)   Serial number of failed request:  29   Current serial number in output stream:  29  

I tried many sizes 750,700,668 etc. Here is xrandr for 668  xrandr -q after running it with 668:

 Screen 0: minimum 320 x 200, current 1280 x 668, maximum 8192 x 8192 VGA1 disconnected (normal left inverted right x axis y axis) LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 304mm x 190mm    1280x800       60.0*+    1024x768       60.0      800x600        60.3      640x480        59.9   TV1 disconnected (normal left inverted right x axis y axis)  

 It does some of the job, but for example System Preferences gets chopped off at the remote Desktop line.

 Thanks
[/SIZE]

---

### Post by realzippy on 2011-08-03
No problem,ask a Mod to move your thread if posted in wrong forum.
Can you post your terminal outputs using code tags?
(it is hard to read)

Try to set framebuffer only:

```
xrandr --fb 1280x700
```

---

### Post by thombark on 2011-08-03
[SIZE=3]thanks for the quick reply.

xrandr -q[/SIZE] [SIZE=3]
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 304mm x 190mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
TV1 disconnected (normal left inverted right x axis y axis)

THEN[/SIZE] [SIZE=3]

xrandr --fb 1280x700[/SIZE] [SIZE=3]
xrandr: specified screen 1280x700 not large enough for output LVDS1 (1280x800+0+0)


Thanks.[/SIZE]

---

### Post by realzippy on 2011-08-03
```
xrandr --fb 1280x700
xrandr: specified screen 1280x700 not large enough for output LVDS1 (1280x800+0+0)
```

I also have this comment:
..."not large enough for output LVDS1"

...**but** it works.

You formerly said that it works partially when you modified some values...?!
So go on...
```
man xrandr
```
gives you information about the syntax,also there are plenty of "xrandr" howtos in the net.
Also "xrandr" afaik is the only possible solution to achieve what you want.
Can 't help you (doubt I could if I where in front of your machine).

If it was my machine,I would grab my screwdriver and look for a
defective contact,or replace the panel....


**Edit:**
One last shot in the dark:

```
xrandr --fb 1280x700 --nograb
```

[I]--nograb
              Apply  the  modifications  without  grabbing  the screen. It avoids to block other applications during the
              update but it might also cause some applications that detect screen resize to receive old values.
[/I]

---

