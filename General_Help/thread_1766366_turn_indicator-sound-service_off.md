---
title: "turn indicator-sound-service off"
date: 2011-05-24
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-05-24
I am trying to turn off the sound icon in the [FONT=Courier New]indicator-applet[/FONT] since it never loads right on the theme for one user and i already set [FONT=Courier New]gnome-volume-control-applet[/FONT] to run at startup to replace it i just cant figure out how to remove it without un-installing it which would effect all users

edit seems resizing the panel will make the default icon work so i make a script using gconf-tool to change the size 2 times at startup to fix it

---

### Post by Frogs Hair on 2011-05-24
I depends on what version of Ubuntu , if using the Classic Gnome desktop environment , right click the icon and remove from panel , but you will loose your mail indicator . This will remove the indicator but not the installed package and it can be restored from the add to panel menu. You are correct about removing the indicator-sound package as it would affect all users.

---

### Post by pqwoerituytrueiwoq on 2011-05-24
ubuntu 10.04 uses gnome 2.something

---

### Post by pqwoerituytrueiwoq on 2011-05-24
is there a way i can restart the *indicator-sound-service*
i tried adding *[FONT=Courier New]killall gnome-panel[/FONT]* to startup but then the panel does not reload

---

