---
title: "Broken themes"
date: 2010-06-03
forum: General Help
---

### Post by Wastedyouthfx0 on 2010-06-03
I was fiddling with ubuntu and I have broken it. =(  I don't know what started it, but now no matter which theme I choose, there appears to be broken buttons in all the themes.  I have attached a screenshot.  

See the light border around the top left?  I double checked a default install in a virtual machine and it doesn't look that way.  The progress bars look off also, and some of the themes have buttons with unreadable colors.

I had been toying with gnome color chooser, Also, I entered some commands from a webpage to change the login screen.

How do I fix this its driving me mad?  


 
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
 
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

    sudo aptitude install plymouth-theme-*
 
    sudo update-alternatives --config default.plymouth
 
    gksu -u gdm dbus-launch gnome-appearance-properties
ng

---

