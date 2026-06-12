---
title: "Default screensaver at logon screen"
date: 2010-12-16
forum: General Help
---

### Post by digitography on 2010-12-16
What I want to do is have a screensaver that will activate at the login screen, after a few mins lack of use.

This can obviously be set for individual accounts, but I cannot figure how this can be done for the login screen.

Suggestions?

Thanks in anticipation

---

### Post by digitography on 2011-03-07
Just to bump this up.
anyone any idea how this could be done?

---

### Post by vivek.pandey on 2011-03-07
did you try system->prefernces->screensaver or you need something else?

---

### Post by digitography on 2011-06-10
What I want is for the screensaver to activate at the login screen, obviously this can be set for individual accounts, but I cannot figure how this can be done for the login screen.

---

### Post by pqwoerituytrueiwoq on 2011-06-10
[FONT=Courier New]sudo cp /usr/share/applications/gnome-screensaver-preferences.desktop /usr/share/gdm/autostart/LoginWindow[/FONT]
logout
for a second you will say what now then the window will open
set it
login
[FONT=Courier New]sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-screensaver-preferences.desktop[/FONT]

references
[http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13]("http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13") (step 3)

---

