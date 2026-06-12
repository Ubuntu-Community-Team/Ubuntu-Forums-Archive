---
title: "Login Screen Help"
date: 2010-02-09
forum: General Help
---

### Post by RedSingularity on 2010-02-09
I just upgraded to 9.10 on my laptop.  I cannot find the option to change my login preferences like i could in previous releases.  It should be in System>Admin>Login Window, but its not.  Where is it found in 9.10?

---

### Post by RedSingularity on 2010-02-09
Nevermind, found it.


1. Logout of your current session and return to the GDM
2. Switch to  the tty command line prompt using Ctrl-Alt-F1
3. Login using your  normal login/password
4. at the command line prompt type: [COLOR=blue]export DISPLAY=:0.0[/COLOR]
5. then type: [COLOR=blue]sudo -u gdm gnome-control-center[/COLOR]
6.  Switch back to the gdm screen using ALT-F7
7. The  gnome-control-center should be loaded. Use it to configure your GDM.
8.  Click on the Appearances icon, in appearances you can change your GDM's  font, theme and background image.
9. Close the gnome-control-center  and login normally.

---

