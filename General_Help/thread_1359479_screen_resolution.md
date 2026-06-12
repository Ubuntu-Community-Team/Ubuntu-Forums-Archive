---
title: "screen resolution"
date: 2009-12-19
forum: General Help
---

### Post by Woe_is_me on 2009-12-19
Hi, 
I'm quite new to ubuntu, and I'll tell you straight, Im pretty stupid when it comes to things like this. 
But my problem is this: 
It as necessary to do a clean install and from 8.something to 9.10. in the previous version my screen resolution worked perfectly fine. But in 9.10 its 800*600 and giving no other options. I've been searching the forums and google but am still not able to solve the problem. This is as far as I have gotten:

```
xxx@Rasputin:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for xxx: 
xxx@Rasputin:~$ xrandr
Screen 0: minimum 320 x 200, current 800 x 600, maximum 2048 x 2048
VGA1 connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3* 
   640x480        59.9  
```

and then what? am I going about this the right way? The graphics card is integrated intel, the monitor was given to me so I don't know the exact model of it either, sorry.
Please someone help, its really starting to hurt my eyes looking at this!

---

### Post by PseudoLemon on 2009-12-19
Did you try to get a new driver? It might help.

---

### Post by dunbrokin on 2009-12-19
[http://ubuntuforums.org/showthread.php?p=8302145](http://ubuntuforums.org/showthread.php?p=8302145)

This did it for me...

---

