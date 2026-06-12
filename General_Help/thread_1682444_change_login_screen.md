---
title: "change login screen"
date: 2011-02-05
forum: General Help
---

### Post by vat with tux on 2011-02-05
I want to change the background of my login screen. Can i do that? If yes then how?
thanking in advance.

---

### Post by stinkeye on 2011-02-05
You can change your login background, theme, etc by entering in the terminal
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
```
Log out then select the style you want at the login from the Appearance window that pops up.



Then log in and execute 
```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```
to remove gnome-appearance-properties from the login window.

---

### Post by vat with tux on 2011-02-05
thanks .:) it works.

---

