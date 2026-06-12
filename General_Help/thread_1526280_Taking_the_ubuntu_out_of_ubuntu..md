---
title: "Taking the ubuntu out of ubuntu."
date: 2010-07-07
forum: General Help
---

### Post by dragos240 on 2010-07-07
I like the ubuntu packages, nuff said. However I'd rather have the default GNOME desktop instead of all the ubuntu extra stuff. This includes:
Notification applet, ubuntu one, the ubuntu themes (ambiance, human, etc.), and the left handed close minimize and maximize options.

---

### Post by amauk on 2010-07-07
the examples you've given are all configuration things that can be changed

but if you want to use upstream software that's pretty much untouched, then try distros like Slackware or Arch

---

### Post by xoros on 2010-07-07
If he wants to stick with the package manager and being able to use .deb's ... maybe Debian would be another choice ?

I'm not sure you can use Ubuntu's packages in Debian though.. or can you?

To change the "left handed close minimize and maximize options" buttons.. (no need for extra software)
```

alt + f2 
gconf-editor

and go to apps > metacity > general > button layout

and change the value to 

menu:minimize,maximize,close
```

---

### Post by hansdown on 2010-07-07
Hi dragos240.

```
sudo apt-get install ubuntu tweak
```

Click apps> system tools> ubuntu tweak> window manager.

You can change which side the buttons are on.

More to follow.

---

### Post by hikaricore on 2010-07-07
> **hansdown said:**
> Hi dragos240.

```
sudo apt-get install **ubuntu-tweak**
```

Click apps> system tools> ubuntu tweak> window manager.

You can change which side the buttons are on.

More to follow.

Fixed.

---

### Post by isbura on 2010-07-08
Linux Mint is an "Ubuntu without Ubuntu" distro that works quite well. It can use the Ubuntu repositories without issue and is in many ways just as user-friendly as Ubuntu but without all the irritating features that are only half-implemented or don't work properly, like Me menus and Ubuntu One.

---

### Post by 3rdalbum on 2010-07-08
I believe what you want is the "Gnome Stracciatella Session", which is pretty close to regular upstream Gnome. You can install it through installing the 'gnome-stracciatella-session' package in Synaptic.

Once that is done, log out. Click on your username and then under the Session menu go to the Stracciatella session. Continue to log in as normal and you'll find yourself transported back in time to before Notify-OSD :-)

---

### Post by Yellow Pasque on 2010-07-08
Use the Ubuntu minimal install (or maybe even Xubuntu) and only install the gnome packages you want.

---

