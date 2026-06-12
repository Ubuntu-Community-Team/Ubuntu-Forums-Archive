---
title: "Is there a way to just boot a web browser and the minimums to run it?"
date: 2011-08-16
forum: General Help
---

### Post by HeretikSaint on 2011-08-16
I was just wondering if there was a way that I can just boot up Google Chrome and the basic minimums to run it (i.e. the network, plugins).  Is there a way that I can boot up Chrome without launching the rest of X?  I figure I'd probably have to have some portion of a window manager to run Chrome considering it is a GUI, but is there a way that to boot it without anything else in the Desktop Environment.  Any and all help is appreciated.

---

### Post by Bachstelze on 2011-08-16
1. Install CLI system
2. Install Xorg and Chrome
3. Put appropriate exec line in ~/.xinitrc
4. startx
5. ???
6. Profit?

---

### Post by HeretikSaint on 2011-08-16
I don't have a ~/.xinitrc, but I do have 
```

/etc/X11/xinit/xinitrc
/etc/xdg/xfce4/xinitrc

```

The first one has almost nothing in it while the second one has quite a large amount of code in it.  Any thoughts of which one to use and where I should begin?

---

### Post by Bucky Ball on 2011-08-16
Try this:

[https://help.ubuntu.com/community/Installation/LowMemorySystems#Install%20an%20Ubuntu%20command-line%20system]("https://help.ubuntu.com/community/Installation/LowMemorySystems#Install%20an%20Ubuntu%20command-line%20system")

You just need a desktop manager and Firefox (or browser of your choice) installed. You probably want synaptics and a few other things but you can add them as you go. There is another page with a neat command to install essential stuff like that but can't find it right now. 

Search for 'minimal install ubuntu' and you should find plenty. Your machine will run like lightning. I had a minimal install with more than you'll have and it got to login in 12 seconds from boot! If you can make an empty partition anywhere you could install it on that and experiment while having a working kernel on another partition. I have four twenty gig partitions for doodling about with that kind of thing. 

Good luck. ;)

---

### Post by HermanAB on 2011-08-16
If you want a small Linux version, use Puppy:
[http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm](http://puppylinux.org/main/Overview%20and%20Getting%20Started.htm)

---

