---
title: "Gnome loading with only time in top right. no menus or icons :("
date: 2010-11-07
forum: General Help
---

### Post by felix.okeefe on 2010-11-07
Ubuntu boots into desktop with autologin. The desktop doesn't display correctly. I get only a purple screen with grey bar at top. In the top right the time is showing but nothing else.
Right click on the desktop does nothing. On the top bar (grey) shows add to panel menu (normal)
Also gnome keyboard shortcuts eg. ALT + F2 do nothing.
To Shutdown the system I have to move to console screen with CTRL + ALT+ F1

Have tried to search through logs myself to no avail.

Forced disk check with $sudo shutdown -rF now

still same issue

Yesterday when it was working normally. I was transferring a large file from another computer (samba) over the wireless connection (slow...)
My router crashed causing the file transfer to freeze.
I deleted the half complete file and used the force quit applet on the file transfer window.

That was the only remotely unusual thing I did that session. For the rest of the time I was watching a film in XBMC.

Please explain what logs / info you need to diagnose
Or what console commands I need to reinstall gnome

Thanks in advance.

---

### Post by Hippytaff on 2010-11-07
you might be able to fix it with
```

sudo apt-get update && sudo apt-get upgrade

```
worth trying before reinstalling gnome :-)

---

### Post by felix.okeefe on 2010-11-08
Helas that didn't help. 
[FONT=monospace]0 [/FONT]upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I have been able to make some launcher icons on the top panel. Got Synaptic to run.
Have reinstalled ubuntu-desktop
See if that fixes things...

---

### Post by felix.okeefe on 2010-11-08
DOH!.. just figured it out.
Gnome was not loading at all. I was seeing an xfce panel.
Something must have got messed up in the login script. It was trying to log me in to mythbuntu
Which is not installed.
I only have mythbuntu-control center and mythtv frontend installed.
All of which I would have seen immediately had it not been for auto-login.

Solution was: add log out button to panel.
use it to log out.
Select Gnome from the login screen
Log in

Voila

---

### Post by dino99 on 2010-11-08
so modify your thread to SOLVED please

---

