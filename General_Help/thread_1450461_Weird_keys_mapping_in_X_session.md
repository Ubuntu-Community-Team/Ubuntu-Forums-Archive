---
title: "Weird keys mapping in X session"
date: 2010-04-09
forum: General Help
---

### Post by ma$$ter on 2010-04-09
hi
I've just upgraded my installed software packages to last version of Lucid and noticed a weird issue: my keyboard keys are all messed up. Although my keyboard layout is still US-105 keys, when I press (for instance) "asdfg", I get "abfhj" and for "ASDFG" I get "1a1b1f1h1j" !? And so on...
This only happens when I am logged as user in a X session.
Root sessions are OK.

Any idea what is going on ?

---

### Post by cornercase on 2010-04-28
Hey, I actually just experienced the same thing running Gnome and tightvncserver.  I never got it to work right with tightvncserver or Gnome.  I ended up killing my Xorg session and then using x11vnc server, which then allowed me to VNC into the box at the login screen.  There, I selected fluxbox (which I had previously installed) and logged in.  Then everything worked.  With Gnome, I managed to get it almost working, but my shift keys wouldn't always act right, and I decided it wasn't worth my time.

Eamon

---

### Post by ma$$ter on 2010-04-29
I had to find a workaround by running Configuration Editor, then went to /apps/gnome_settings_daemon/plugins/keyboard and unchecked 'active' variable. Then I was good to go.
Bottom line, gnome_settings_daemon is a buggy bitch.

---

