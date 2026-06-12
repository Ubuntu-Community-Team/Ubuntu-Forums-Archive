---
title: "Changed my login screen to Ubuntu (Safe Mode)...now I can't change it back..."
date: 2011-07-25
forum: General Help
---

### Post by jmarcedwards on 2011-07-25
I was fooling around with my Login default screen and set my login to "Ubuntu (Safe Mode)".  Now, it seems as if the system does not grant me the authority to change it back to another default login.

Can someone tell me how to fix this?

Thanks, Marc

---

### Post by Theredbaron1834 on 2011-07-25
The only way I know to do this is, from the term, run the command:
```
sudo ln -s /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/

```This makes the gnome-apperance-properties manager auto load when the loginwindow starts.
Log out, and gnome-apperance properties will load on the login screen. Change your background and log in and run this command in a term:
```
sudo rm -rf /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```
It removes the autostart so you don't have to exit everytime.

If anybody knows of a better way, I would love to know too.

---

### Post by raja.genupula on 2011-07-25
goto system settings->System-> login screen 
unlock it and at at **SELEC**T choose your ubuntu

---

### Post by Theredbaron1834 on 2011-07-25
Ugh, yeah, I was thinking he said he couldn't change his background. Sorry.
What raja said.

---

### Post by Eddict on 2011-07-26
try this one. kudos to that poster... :D

[http://ubuntuforums.org/showpost.php?p=10475376#2](http://ubuntuforums.org/showpost.php?p=10475376#2)

---

### Post by jmarcedwards on 2011-07-26
Perfect.  It worked.  Many thanks.

---

