---
title: "ahhh.. update + XGL messed up my dapper!"
date: 2006-06-14
forum: General Help
---

### Post by torx on 2006-06-14
So i was updating half way through and all of a sudden, XGL/Compiz decides to crash to login. When i tried to relogin, i get an error and i thought. okay, XGL must have been screwed. But that's okay. But when i login back to GNOME, i realize that my entire 3d acceleration is screwed.

This is what i get from fglrxinfo

display: :0.0  screen: 0
OpenGL vendor string: (null)
OpenGL renderer string: (null)
OpenGL version string: (null)

Previously, it would show ATI Technologies and blah blah. Also, glxgears gives a blank screen. I tried to grab all updates, but there arnt any available (even though i clearly crashed halfway through the installation).

So please help me! I think all i need to do is to reinstall the packages that crashed during the update. But how do i find out which is broken???

---

### Post by DarthMandeep on 2006-06-14
What does the Device section of the /etc/X11/xorg.conf file say? My guess would be that it's no longer using the proper drivers.

---

### Post by blackjack6.21.91 on 2006-06-14
I'm not exactly sure about how to fix XGL, but you can locate broken packages very easily in synaptic (System --> Administration --> Synaptic Package Manager)

Click the "custom" button in the bottom of the left panel and then select broken.  Highlight all of them (ctrl A), right click, and install!

Good luck w/ XGL.
blackjack

---

### Post by Patrick-Ruff on 2006-06-14
if all else fails, your system suddenly gets unstable or something like that, theres always recovery mode... ;)

---

