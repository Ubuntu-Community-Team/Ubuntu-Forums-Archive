---
title: "Loading a modmap file at login"
date: 2010-04-03
forum: General Help
---

### Post by flyingtabmow on 2010-04-03
I'm trying to load an xmodmap file on login.  I can't use .Xmodmap or similar (although they work) because the loading is conditional (based on whether the login is local or remote, through XDMCP).  Unfortunately, I can't seem to find any way of loading an xmodmap file on login by other means... adding an xmodmap call to Startup Applications doesn't appear to do anything, nor does adding it to .xprofile, .profile, .xsession, .xinitrc, .bash_profile, .bashrc, /etc/X11/Xsession, /etc/gdm/Xsession, or /etc/gdm/PostLogin/Default.  Although I'm sure the call runs in most of these cases, it seems gdm or Gnome or something is overriding it at the last minute.  Loading it from the terminal by hand does work... so it's not the modmap file that's at fault.  I just can't find a suitable place to run the poor thing at login so that it sticks.  Anyone know what's going on?

---

