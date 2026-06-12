---
title: "Shut down the computer"
date: 2010-03-03
forum: General Help
---

### Post by nmyrick on 2010-03-03
Can someone tell me what the command is to activate the "shut down the computer" window, which comes up if you use the shut down the computer launcher that you can add to a panel.  

I'm asking for this because I am trying to create a a launcher to do the same for Avant Window Navagator.

Thanks,
nmyrick

---

### Post by frt975 on 2010-03-03
Lock screen:```
gnome-screensaver-command --lock
```
Logout:```
gnome-session-save --kill
```
Shutdown: ```
gnome-session-save --shutdown-dialog
```

---

### Post by nmyrick on 2010-03-04
Thank you very much!  We've just created a new applet for Avant Window Manager.

---

### Post by nmyrick on 2010-03-04
Your welcome.  Have you tried Avant Window Manager?  It is awesome!  It is a linux dock that is like the dock at the bottom of a Mac desktop.  You can get it from the Ubuntu Software Center.  If you download Avant Window Manager, then you will also want to download the AWM Manager, which is for Avant.

---

