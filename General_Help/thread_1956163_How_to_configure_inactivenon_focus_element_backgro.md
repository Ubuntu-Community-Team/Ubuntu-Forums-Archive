---
title: "How to configure inactive/non focus element background/foreground"
date: 2012-04-10
forum: General Help
---

### Post by mjsilverstri on 2012-04-10
How to configure my theme's inactive background and foreground color? In eclipse, when I have inactive element, it shows up as white text on light grey background. That is hard to read.

I have attached a screen shot.

[http://imageshack.us/photo/my-images/713/screenshotat20120410094.png/](http://imageshack.us/photo/my-images/713/screenshotat20120410094.png/)

I am running ubuntu 11.10 and gnome shell.

---

### Post by ostanley on 2012-04-22
Found the solution here:
[http://ubuntuforums.org/showthread.php?t=1856281](http://ubuntuforums.org/showthread.php?t=1856281)

open /usr/share/themes/<your theme, e.g. Ambiance>/gtk-2.0/gtkrc
In "default" section change[INDENT]base[ACTIVE]      = shade(0.8, "#F2F1F0")
[/INDENT]Log out or change your style in order to reload new settings.

---

