---
title: "GDM Brightness"
date: 2009-07-31
forum: General Help
---

### Post by redsky1302 on 2009-07-31
My laptop running jaunty has some curious brightness behaviour that I hope you guys can help me with.  During the boot sequence, the initial brightness from bios all the way to GRUB is fine. However, during the ubuntu splash (the one with the status bar), the brightness suddenly goes to maximum and remains that way.  When I log in, the brightness goes down to 5% (as I set it that way in the Power Management utility). If I log out, the brightness of the login screen correctly remains at 5%.  My question is: Is there a way for me to set the initial brightness of ubuntu? I don't like that sudden surge of brightness during the boot sequence till I log in.

---

### Post by afeasfaerw23231233 on 2009-07-31
Press alt-f2 and run **gconf-editor**
On the left panel open **/ > apps > gnome-power-manager > backlight**
you can adjust the brightness by modifying the value of **brightness_ac** and **brightness_battery**. You can also disable or enable the auto dimming function.

P.S. It takes effect immediately. You don't need to restart the computer. :)

---

### Post by redsky1302 on 2009-08-02
It doesn't seem to affect the brightness of the ubuntu splash, even when I do a sudo gconf-editor and modify the backlight settings.

---

### Post by aadityabhatia on 2010-04-07
I'm facing the same issue in Karmic and Lucid at this point, with no apparent solution.

Here's the related bug:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/464577](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/464577)

There's an option in Launchpad to specify that this bug affects you.

--
Aaditya
[http://www.dragonsblaze.com/](http://www.dragonsblaze.com/)

---

### Post by swmail on 2010-05-04
To set the initial brightness of gdm you can use the command:
gksudo -u gdm dbus-launch gconf-editor

and set the key /apps/gnome-power-manager/backlight/brightness_ac to value 0..100

---

### Post by growingneeds on 2010-05-08
Thank you, swmail! Your terminal command works like a charm. Although... The interface that was brought up looks strikingly similar to Windows Registry. But then, I am very grateful for not needing to set my login screen at maximum brightness each time I boot up Lucid Lynx.

---

