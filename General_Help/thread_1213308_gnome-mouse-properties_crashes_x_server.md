---
title: "gnome-mouse-properties crashes x server"
date: 2009-07-14
forum: General Help
---

### Post by MES5464 on 2009-07-14
I am running Jaunty on a Lenovo X60 Tablet. I have to use the xorg.conf to allow the stylus to work with the built in Wacom tablet. Everytime I try to open gnome-mouse-properties the x server crashes. I have tried:

System > Preferences > Mouse
Terminal with sudo gnome-mouse-properties
Synaptic reinstall of gnome-control-center

I am convinced there is something in my xorg.conf that is killing me but I have not idea what it is. Can anyone help?

---

### Post by Favux on 2009-07-15
Hi MES5464,

Cleaned it up for you.  There were a few problems.

You had usb on but the X60t is a serial tablet pc.  You had two "ServerLayout"'s.  And a bunch of unnecessary Wacom entries.

Hopefully this will help.

Be sure to back up your xorg.conf.  Then compare the two to see what I did and to make sure I didn't make a goof.

Good luck!

---

