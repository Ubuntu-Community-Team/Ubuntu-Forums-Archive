---
title: "Unity bar on wrong screen...."
date: 2011-09-21
forum: General Help
---

### Post by searayman on 2011-09-21
I installed natty and got my dual screen set up after installing my restricted drivers, but my unity bar is on the right screen which puts it in the middle....

any ideas how i can fix this and move it to the left screen?

---

### Post by Hugh971 on 2011-09-21
Had this same problem myself.

To fix it run 

```
xrandr
```

to list your screens and then run 

```
xrandr --output DVI-1 --primary
```
(swapping DVI-1 for the screen you want as primary)

---

### Post by searayman on 2011-09-21
> **Hugh971 said:**
> Had this same problem myself.

To fix it run 

```
xrandr
```

to list your screens and then run 

```
xrandr --output DVI-1 --primary
```
(swapping DVI-1 for the screen you want as primary)

OK so I tried the xrandr thing and got all this. And do not know what to make of it:

mike@buck:~$ xrandr
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 2560 x 2560
DFP1 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1280x960       60.0 +   75.0  
   1280x800       60.0 +   75.0  
   1152x864       60.0 +   75.0  
   1280x768       59.9 +   74.9  
   1280x720       60.0 +
   1152x648       60.0 +
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     70.0     60.3  
   720x480        60.0  
   640x480        75.0     72.8     60.0  
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 disconnected (normal left inverted right x axis y axis)
CRT2 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0 +   75.0* 
   1280x720       60.0 +
   1280x960       75.0     60.0  
   1280x800       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       74.9     59.9  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   720x480        60.0  
   640x480        75.0     60.0  
TV disconnected (normal left inverted right x axis y axis)
CV disconnected (normal left inverted right x axis y axis)
mike@buck:~$

---

