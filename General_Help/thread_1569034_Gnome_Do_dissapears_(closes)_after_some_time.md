---
title: "Gnome Do dissapears (closes) after some time"
date: 2010-09-06
forum: General Help
---

### Post by kabeza on 2010-09-06
Hi
I'm having some trouble with Gnome Do (but I think that maybe something else is causing this)

When my PC starts, I can see the Gnome Do icon in the panel, as you can see in the following screenshot:

[[IMG]http://imgur.com/yKf8Ys.jpg[/IMG]](http://imgur.com/yKf8Y.jpg)

After some time, this icon dissapears and seems Gnome Do closes, because can't launch it with the shortcut key I am used to use for it

[[IMG]http://imgur.com/svgVms.jpg[/IMG]](http://imgur.com/svgVm.jpg)

Does anyone know how I should do to trap the cause of this problem? which logs should I check, etc.?

Thanks a lot in advance,

---

### Post by grimslider75 on 2011-11-27
I have this problem to.... Any one know an answer?  :confused:

---

### Post by kpuz on 2011-11-27
You can start gnome-do in debug mode by typing
```
gnome-do --debug
```

When it crashes check to see what the error was. I remember when this was happening to me I had a problem with the youtube plugin.  I unchecked the youtube plugin and everything worked fine after that.

---

