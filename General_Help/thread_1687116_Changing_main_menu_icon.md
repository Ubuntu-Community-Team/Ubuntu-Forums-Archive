---
title: "Changing main menu icon"
date: 2011-02-13
forum: General Help
---

### Post by Spyderkid on 2011-02-13
I've tried many many many ways of changing the main menu icon but I cant manage it! I've got one but I just can't get it to change i've tried gconf, i've tried going to /usr/share/icons/gnome/places and change the icon start-here.png and tried some other ways does anyone know how to change it in Ubuntu 10.10 preferably not using gconf.

*thanks!*

---

### Post by Spyderkid on 2011-02-13
But if you do know a way with gconf then i'd like to hear it anythings an option i guess...

---

### Post by An Sanct on 2011-02-13
Giving in to gconf ;)

The root icons are theme related.
Here is a way, already mentioned on this forum
> [http://ubuntuforums.org/showthread.php?t=533247](http://ubuntuforums.org/showthread.php?t=533247)

If you would like to change application icons, you can also right click on the menu, select "Edit Menus", now you will see all the applications, that are there, also the hidden ones.

---

### Post by balaknair on 2011-02-13
Ubuntu Tweak lets you change the icon via a simple GUI(in the 'GNOME Settings' section).
Install with the downloadable .deb file
[http://launchpad.net/ubuntu-tweak/0.5.x/0.5.10/+download/ubuntu-tweak_0.5.10-1_all.deb](http://launchpad.net/ubuntu-tweak/0.5.x/0.5.10/+download/ubuntu-tweak_0.5.10-1_all.deb)

or via the PPA at
[https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

In the terminal, run
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update && sudo apt-get install ubuntu-tweak

---

### Post by Spyderkid on 2011-02-13
I've looked at that post An Sanct (it didn't work)

balaknair ill give yours a go

---

### Post by Spyderkid on 2011-02-13
It worked!!!!!! Finally

---

### Post by balaknair on 2011-02-13
OK
Good to know it helped.

Have fun :D

---

### Post by Spyderkid on 2011-02-14
came up with an even better solution! :)

to go to the place where the themes are stored
[COLOR="Red"]usr[/COLOR] > [COLOR="red"]share[/COLOR] > [COLOR="red"]icons[/COLOR] > and then compress the theme you want to edit into your home folder, then extract and edit away changeing as many icons as you want :D

then when you've done editing compress and install the new theme :D

---

### Post by Spyderkid on 2011-02-14
however came up with one more problem how do you edit the background to the things you put on your panel e.g. indicator applet, and the indicator applet session.

how do you change the image behind them on these because they wont change along with my taskbar.

---

### Post by jerrrys on 2011-02-14
GIMP will do a lot of things when customizing.  with just a handful of tools you can do

[ATTACH]183465[/ATTACH]

---

