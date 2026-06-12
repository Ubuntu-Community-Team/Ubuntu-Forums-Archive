---
title: "Broken Packages Help?"
date: 2010-07-28
forum: General Help
---

### Post by Ocelot_P on 2010-07-28
In my synaptic package manager it tells me i have two broken packages upon openeing and use the "broken" filter to locate and fix them ( capplets-data and gnome-control-center) When i do that i get the message attached to this post. Also at the bottom of the details that cannot be viewed by the screen shot it says this:

     Package indicator-applet is not configured yet.
dpkg:   error processing indicator-applet session   (--configure):
  dependency problems - leaving unconfigured
Errors were encountered while processing:
   gnome-control-center
   gnome-panel
   indicator-applet
   indicator-applet-session



I am very new to linux and I'm sure there is an easy fix to this, I just don't know where to begin.

---

### Post by philinux on 2010-07-28
Open a terminal, apps>accessories.

```
sudo dpkg --configure -a
```

Post back all the errors. Wrap the text in code tags. (The # key in the reply pane.)

---

### Post by Ocelot_P on 2010-07-28
Im sorry I forgot to say that im using version 10.4, if that even helps. I entered the:  

 sudo dpkg --configure -a


i got this: (attached)

---

### Post by Ocelot_P on 2010-07-28
ismael@ismael-laptop:~$ sudo dpkg --configure -a
[sudo] password for ismael: 
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on libgnome-window-settings1 (= 1:2.30.0-0ubuntu4); however:
  Version of libgnome-window-settings1 on system is 1:2.30.1-0ubuntu1.
 capplets-data (1:2.30.1-0ubuntu1) breaks gnome-control-center (<< 1:2.30.1-0ubuntu1) and is installed.
  Version of gnome-control-center to be configured is 1:2.30.0-0ubuntu4.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-applet:
 indicator-applet depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
dpkg: error processing indicator-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-applet-session:
 indicator-applet-session depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
 indicator-applet-session depends on indicator-applet (= 0.3.7-0ubuntu1); however:
  Package indicator-applet is not configured yet.
dpkg: error processing indicator-applet-session (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-control-center
 gnome-panel
 indicator-applet
 indicator-applet-session


Im sorry, I don't know what a "code tag" is. but this was the error that came up after : 

    sudo dpkg  --configure -a

---

