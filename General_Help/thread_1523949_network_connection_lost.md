---
title: "network connection lost"
date: 2010-07-04
forum: General Help
---

### Post by tjh196 on 2010-07-04
hi, i just installed ubuntu 10.04 on my laptop. everything was working fine until i installed firestarter. i didnt like it and uninstalled it. when i did that i lost my wireless signal icon at the top of the screen, firefox starts up in offline mode, and limewire says that network connection is lost. i just want it back the way it was before installing firestarter. please help, i dont want to reinstall ubuntu if i dont have to. thanx

---

### Post by J V on 2010-07-04
You should be able to restart and get it back, if not, you may be missing the notifications, rightclick the bar at the top and press "Add to panel" - select "Notification area"

Yet another reason why no-one should use firestarter...

---

### Post by ajgreeny on 2010-07-04
Did you make any changes to your settings when you ran firestarter?

If so you may need to purge iptables with ```
sudo iptables -F
``` to get things back where they should be.

As J V says, firestarter is not the way to do things any more; I'm not sure it ever was, but if you need to make any changes now, use ufw or gufw.  If you are not running a server, you probably don't need to do anything; just leave things as they are in a default setup.

---

