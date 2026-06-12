---
title: "Customizing the Login screen with Compiz"
date: 2011-01-24
forum: General Help
---

### Post by silkworm2.5 on 2011-01-24
Hi all.
I've been trying to customize my Login screen with Compiz In Ubuntu 10.04. I used the following codes in a terminal to show me the Appearance and Compiz Config screens:

```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
``````
sudo cp /usr/share/applications/ccsm.desktop/usr/share/gdm/autostart/LoginWindow
```This displays them in the Login screen. I'm having a couple of problems though.
1. Visual effects reset to none when I reboot. (I want to have the Login box semi-transparent)
2. Even though I use compiz to grab the class of the login box, it wont set it to be transparent. 
3. Now the GDM's theme controls my window border, and progress bars.

Any advice please?
Note: commands were found at this website: [http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html](http://www.ubuntugeek.com/how-do-you-change-the-boot-splash-screen-image-for-10-04-lucid-lynx.html)

---

