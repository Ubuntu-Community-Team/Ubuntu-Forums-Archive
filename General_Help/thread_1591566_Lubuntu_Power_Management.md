---
title: "Lubuntu Power Management"
date: 2010-10-09
forum: General Help
---

### Post by slooksterpsv on 2010-10-09
I know Lubuntu is still in a phase where everything isn't going to work, but I was wondering if someone had some helpful tips/hints or fixes for the issues I'm having with Power Management.

1. I've set the options in gnome-power-preferences to put the computer to sleep after 10 min, but it doesn't sleep. It's 10.10 Beta 2 32-bit. Let me know what information you need from it.

---

### Post by slooksterpsv on 2010-10-09
EDIT: Guess I don't try hard enough hehe. I fixed it by installing:
xfce4-power-manager - it works now, I just ran that, clicked the battery, configured it, and it's working perfect now!

---

### Post by bwiesem on 2010-10-15
> **slooksterpsv said:**
> clicked the battery, configured it

Unfortunately, in the default settings of both gnome power manager and xfce4 power manager, that battery symbol in the control panel is only shown if a battery is present, and Lubuntu comes without a menu entry for power management settings. So, if you're running Lubuntu on a desktop computer, the desktop environment gives you no option to configure power management. Instead, you have to run gnome-power-preferences in a terminal (or xfce4-power-manager-settings, respectively, if you've chosen to install xfce4 power manager).

I've decided to use xfce4 power manager on my freshly-installed Lubuntu 10.10 box, but I still have two unsolved problems. The smaller one is that I would like to start it automatically while booting, maybe someone can tell me how to do it. The bigger problem is that I would like to get rid of the pre-installed gnome power manager, but synaptic tells me I have to remove lubuntu-desktop in order to do that. This is astonishing! Isn't there a way to uninstall gnome power manager without throwing away the whole Lubuntu desktop environment?

---

### Post by slooksterpsv on 2010-10-16
> **bwiesem said:**
> ...

I've decided to use xfce4 power manager on my freshly-installed Lubuntu 10.10 box, but I still have two unsolved problems. The smaller one is that I would like to **start it automatically while booting**, maybe someone can tell me how to do it. The bigger problem is that **I would like to get rid of the pre-installed gnome power manager, but synaptic tells me I have to remove lubuntu-desktop in order to do that**. This is astonishing! Isn't there a way to uninstall gnome power manager without throwing away the whole Lubuntu desktop environment?

For your first issue, I believe there's a configuration file you can edit to make it start automatically, I wonder if lxde uses like I wanna say .bashrc or that.

For the second issue, is it just the metapackage it wants to remove or does it say after removal 550MB will be free or something like that? The reason I ask is cause it may just be the metapackage and not the actual items installed

---

### Post by bwiesem on 2010-10-16
Now I've found the solutions for my problems :)

Both gnome and xfce4 power manager come with .desktop files in /usr/share/applications - but these contain a line like
```
OnlyShowIn=GNOME;XFCE;
```
which prevents the menu entries from showing up in LXDE. So, in order to get a link to power management configuration in the menu, you have to remove that line.

For autostart, gnome power manager comes with a another .desktop file in the hidden subdirectory ~/.config/autostart in the user's respective home directory. Again, a line similar to the one mentioned above prevents it from working in LXDE and has to be removed. Xfce power manager didn't provide such a .desktop file for autostart, so I wrote one myself:

```
[Desktop Entry]
Name=Xfce4 Power Manager
Comment=Power management daemon
Icon=xfce4-power-manager
Exec=xfce4-power-manager
Terminal=false
Type=Application
Categories=
```

I saved it as "xfce4-power-manager.desktop" in the hidden autostart directory and it works fine.

> **slooksterpsv said:**
> it may just be the metapackage and not the actual items installed

You're obviously right :) - instead of synaptic, I used apt-get now to find out that gnome-power-manager and lubuntu-desktop together are only 4604KB together, so "lubuntu-desktop" can't be all the files installed for the desktop environment. I've removed it together with gnome-power-manager and everything works :)

---

### Post by dschaller on 2010-10-27
This is a really helpful thread. Thanks to those who have contributed. I have Lubuntu 10.10 on an old Compaq Armada M700 laptop. It would not recover properly from suspend (the display would never come back up). I switched to xfce4-power-management using the instructions in this thread and suspend now works properly.

---

### Post by amjjawad on 2011-03-08
Very useful thread indeed. I didn't expect to fix the Power Management-Issue in LXDE in few simple steps like these.

Lubuntu 10.04 here with the latest Kernel.

***gnome-power-management*** is installed by default with Lubuntu 10.04. However, it's not added in ***Preferences Menu***.
Above all, Power Management does not work "out of the box" in Lubuntu 10.04. Even if you set the display to sleep if inactive for 10 minutes, it will never sleep at all. Yes, I'm talking about new fresh Lubuntu 10.04 installation.

To make it easier for everyone else, this is what I did to add **"Power Management"** to ***Preferences Menu***:

1) Terminal
2) ```
cd /usr/share/applications
```3) ```
gksudo leafpad gnome-power-preferences.desktop
```4) Enter your ROOT's password.
5) File > Save As > ***Save a Backup Copy of the file ***(gnome-power-preferences.desktop) - [B][I]for example "gnome-power-preferences2.desktop".
[/I][/B]6) Remove 
```
OnlyShowIn=GNOME;XFCE;

```From the file and then Save.
7) You're done. A new entry will be added (Power Management).

Once I've done that, the display went to sleep mode after X minutes.

By the way, I don't have "~/.config/autostart" at all. But as far as I can tell, I don't need it because the Power Management does work now.

---

