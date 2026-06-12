---
title: "GDM login starts and then goes back to login"
date: 2011-02-07
forum: General Help
---

### Post by dchenbecker on 2011-02-07
I just upgraded from 10.04 to 10.10 this morning and after the upgrade I can't log in via GDM. If I log in it seems to work and the screen goes black, but then it goes right back to the login screen. The gdm log shows that something is throwing a SIGTERM (15):

```

** (gdm-simple-greeter:11342): DEBUG: GdmGreeterSession: user authorized
** (gdm-simple-greeter:11342): DEBUG: GdmGreeterLoginWindow: user now authorized
** (gdm-simple-greeter:11342): DEBUG: GdmGreeterLoginWindow: starting session
** (gdm-simple-greeter:11342): DEBUG: GdmGreeterClient: Calling StartSessionWhenReady
** (gnome-session:11323): DEBUG: GdmSignalHandler: handling signal 15
** (gnome-session:11323): DEBUG: GdmSignalHandler: Found 1 callbacks
** (gnome-session:11323): DEBUG: GdmSignalHandler: running 15 handler: 0x419ef0
** (gnome-session:11323): DEBUG: Got callback for signal 15
** (gnome-session:11323): DEBUG: GsmManager: Logout called
** (gnome-session:11323): DEBUG: GsmManager: requesting logout
** (gnome-session:11323): DEBUG: GsmManager: ending phase RUNNING

```

I can't figure out what is throwing the signal, but the interesting thing is that if I stop GDM and log in on the console, I can run startx and my session runs fine (I'm typing this message from firefox). Any ideas on how to determine what is throwing the signal? I tried poking around in /var/log but I can't find anything that seems relevant.

Thanks,

Derek

---

### Post by dchenbecker on 2011-02-18
In case anyone else runs into the same issue:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/663135](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/663135)

In my case I had an extraneous "/etc/X11/Xsession.d/70fglrx_32bit_dri" directory that was trying to load some 32 bit drivers and crashed X.

---

