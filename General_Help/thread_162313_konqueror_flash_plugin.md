---
title: "konqueror flash plugin"
date: 2006-04-18
forum: General Help
---

### Post by moon_dog on 2006-04-18
how do you get konqueror to see the flash plug in? all the posts i've read so far say Settings-->configure konqueror-->plugin, but i don't see the plugin icon.  i'm using konqueror 3.5.1 on Gnome, not KDE.  for some reason, my copy of konqueror has no plugin icon.  is there another way to install the flash plugin?

---

### Post by Ulokye on 2006-04-18
[http://www.kde-apps.org/content/show.php?content=29123](http://www.kde-apps.org/content/show.php?content=29123)

---

### Post by moon_dog on 2006-04-18
the page isn't very clear on how and where to apply the patch.

---

### Post by cwidger on 2007-06-06
You need:

sudo apt-get install konqueror-nsplugins

then

sudo apt-get install flashplugin-nonfree

then

Settings->Configure Conqueror..... Plugins..... Scan for new plugins

That's all there was to it. I'm using 7.04 Fiesty Fawn

---

