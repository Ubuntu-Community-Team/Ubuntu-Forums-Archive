---
title: "No panels after 11.04 upgrade"
date: 2011-05-01
forum: General Help
---

### Post by guru Hari on 2011-05-01
Hello world. So, after upgrade from 10.10 to 11.04, after I login there are no panels. Only thing I can do is right click and bring down a drop-down menu. So I created firefox launcher. I've tried to reboot in recovery mode, in some display safe mode, and all panels and windows look fine, with all window buttons, so I tried to change display driver from current recommended to 173 (Nvidia). After reboot problem is still here. I also tried to rename new xorg.conf and replace it with what I think was pre-upgrade one in /etc/X11 but nothing helped. Hope someone can help me.

---

### Post by epud on 2011-05-01
Have a go at logging out from the system. Then when you choose your user at the bottom of the screen you can choose a different session. Try ubuntu-classic and see if you get the panels back. I had a similar problem when playing around with compiz. To solve it opened up the compiz manager, choose preferences, from the drop down chose unity then hit the "Reset to defaults" button.

Either way, to access a terminal without panels double click a folder on your desktop (if you have one). Then navigate yourself to /usr/share/applications. In there you should find Terminal.

Hope some of the above stuff helps.

---

### Post by r0t on 2011-05-07
I have what might be the same problem. No panels at all. In fact, logging in to Unity doesn't even give me a desktop, just the background from the login screen. Pressing <ctrl> <alt>-<backspace> the desktop background from Gnome appears for half a second, before I'm sent back to login. Logging in to ”classic mode” or ”failsafe” gives me a desktop, but no panels.

I'm able to start a terminal window from the context meny when right clicking the desktop, and from there I've run Nvidias settings program (I have a Nvidia card) and I've tried almost every possible setting there, just to check, but not much changes (apart from the Xinerama mode that seems to break 11.04 in funny ways).

Any suggestions on how to start troubleshooting?

---

### Post by Gammew on 2011-06-07
I got it working by starting 'Panel' in /usr/share/applications. Works smooth except for some temperature meters :)

---

