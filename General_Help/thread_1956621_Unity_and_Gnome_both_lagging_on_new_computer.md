---
title: "Unity and Gnome both lagging on new computer"
date: 2012-04-11
forum: General Help
---

### Post by SGFzc2U= on 2012-04-11
Hello,

I have recently bought a new computer. Now when I play games (sauerbraten) on fullscreen, I easily get ~200 fps all on maximum @1920x1080, but when it's on a window, it clearly lags. The same problem can also be seen when moving windows or watching youtube. :confused:

Info:
Club 3D Radeon HD 6770
Intel i3 2120 (3.3GHz)
Asus P8H77-M LE
4 GB Kingston DDR3

Ubuntu 11.10 32-bit (I know I can install 64-bit version)
AMD Catalyst 12.3

---

### Post by dino99 on 2012-04-11
so i suppose that the graphic driver is correctly activated (sudo jockey-gtk). Which one is used ? Have you some ppa activated too ?

you should get some usefull errors logged either into .xsession-errors (/home) or into /var/log/

---

### Post by SGFzc2U= on 2012-04-11
Actually I downloaded the newest driver from AMD's website. 
.xsession-errors: [http://pastebin.com/8NCs5qeX](http://pastebin.com/8NCs5qeX)

---

### Post by SGFzc2U= on 2012-04-11
Now it starts getting really odd... I reinstalled Ubuntu, and without the drivers moving windows don't lag... Then again sauerbraten lags & none of the settings actually do anything...

---

### Post by SGFzc2U= on 2012-04-11
Found it!

If anyone else is having this problem and can't find help,
[http://ubuntuforums.org/showthread.php?t=1860437](http://ubuntuforums.org/showthread.php?t=1860437)

I should have searched a bit longer at first. Sorry!
The only problem is the lack of vSync on unity, but it doesn't bug me. Game vSync in sauerbraten still works.

---

