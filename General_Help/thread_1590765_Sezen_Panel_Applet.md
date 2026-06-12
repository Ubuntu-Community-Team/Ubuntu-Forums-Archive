---
title: "Sezen Panel Applet"
date: 2010-10-08
forum: General Help
---

### Post by amdemas on 2010-10-08
Hi, 

I had installed a panel app for sezen allowing for search function. Here is the link I used to install it:

[http://www.webupd8.org/2010/08/sezen-applet-is-ready-for-ubuntu-1010.html](http://www.webupd8.org/2010/08/sezen-applet-is-ready-for-ubuntu-1010.html)

Well last night I booted up and it just disappeared? When I go to add it back to the panel it isn't in the list anymore and when I do the reinstall process again it says nothing changed. So what else can I do?

Thanks for the help

---

### Post by amdemas on 2010-10-08
The panel encountered a problem while loading "OAFIID:GNOME_Panel_SezenApplet"

I got this and I hit delete by accident and now it has disappeared and reinstalling everything wont bring it back. Is there anything I can do?

I followed these steps 
sudo apt-get install gnome-applets-dbg
gdb /usr/lib/gnome-applets/sezenapplet

then type "start". Once the program is running, return to the dialog that asked you to reload the applet and accept to reload the applet. If you did not have this dialog, then simply add the applet to the panel. 

The error came up no symbol loaded.

So what else can be done?

---

### Post by amdemas on 2010-10-08
Thanks to Andrew at Webupd8 his answer was:

The applet comes bundled with all the other Gnome applets in the "gnome-applets" package. And Ubuntu 10.10 now has a newer version of this gnome-applets package than the package in which sezen is integrated in. So the Sezen Applet devs will have to update it for the new version. I could just bump the version to make it install, but that wouldn't be right..

---

### Post by afrodeity on 2010-11-07
was just wondering about this, really missing sezen applet, one of the best additions to my panel, hope it gets updated soon.

---

