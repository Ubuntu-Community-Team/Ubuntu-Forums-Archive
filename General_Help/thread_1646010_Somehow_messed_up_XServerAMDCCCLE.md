---
title: "Somehow messed up XServer/AMDCCCLE??"
date: 2010-12-15
forum: General Help
---

### Post by Inkybro on 2010-12-15
Hey.

Yesterday my friend decided to try and be clever and use a shortcut that he uses for something on his Mac on my Ubuntu box. The shortcut was Alt+Ctrl+F1 which shutdown Ubuntu's GUI and took me to a console where I had to login.

I logged back into my user account and tried "startx" but it complained about some /tmp/X0.lock file (or something of that nature). I got lazy and didn't want to reboot so I tried deleting the lock file and when I rebooted, my dual monitors wouldn't work right.

The dual monitors displays both desktops fine. Xinerama IS enabled, but I CANNOT move my mouse between screens. Even stranger is at one point the Login box appeared on the other monitor, but once I pull my mouse to the other screen, it won't go back to the one with the login screen.

I also can't drag anything into other workspaces anymore, though I can navigate between them just fine.

I need to fix this, as it really messes up my productivity levels >.<

Edit: I'd also like to note that I've tried to turn the dual monitor support off in AMDCCCLE, reboot, and re-enable everything. This leads me to believe that somehow I need to reset the default settings or reinstall, but I don't know exactly what I need to do or how to do it.

---

