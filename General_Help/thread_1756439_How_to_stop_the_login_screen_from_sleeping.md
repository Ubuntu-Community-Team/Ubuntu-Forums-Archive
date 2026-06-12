---
title: "How to stop the login screen from sleeping"
date: 2011-05-12
forum: General Help
---

### Post by Azdour on 2011-05-12
Hi,

We use several Ubuntu 10.04 machines at exhibitions. Sometimes the screens are left at the login screen and after a while the display turns off/sleeps. Is there anywhere we can stop this? I know if we log into the machine I can stop the screen saver and tell the power manger to not make the display go to sleep, but this does not have any impact on the login screen going to sleep.

I would greatly appreciate any pointers or help, thanks.

---

### Post by sisco311 on 2011-05-12
You have to disable the screensaver as user gdm.

There are many methods. For example,  you can add gnome-screensaver-preferences to GDM's autostart:
```
sudo cp /usr/share/applications/gnome-screensaver-preferences.desktop /usr/share/gdm/autostart/LoginWindow/
```

Log out back to GDM. The screensaver preferences window will pop up. Disable the screensaver, close the window and log back in. When you're done and want the window to stop opening with GDM run this:
```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-screensaver-preferences.desktop
```

A much faster approach would be to change the value of the /apps/gnome-screensaver/idle_activation_enabled and /apps/gnome-screensaver/lock_enabled gconf keys:
```
sudo -u gdm gconftool-2 --set --type "bool" /apps/gnome-screensaver/idle_activation_enabled "false"
```
```
sudo -u gdm gconftool-2 --set --type "bool" /apps/gnome-screensaver/lock_enabled "false"
```

Or you can try to run gconf-editor or gnome-screensaver-properties as user gdm while you are logged in:
```
xhost +
sudo -u gdm dbus-launch gnome-screensaver-preferences
sudo -u gdm dbus-launch gconf-editor
xhost -
```

And finally :) you can try to start a new X session as user gdm. You have to start it from a virtual terminal (Ctrl+Alt+F1):
```
sudo -u gdm xinit /usr/bin/ck-launch-session /usr/bin/gnome-screensaver-properties -- :10 vt10
```
```
sudo -u gdm xinit /usr/bin/dbus-launch /usr/bin/ck-launch-session /usr/bin/gconf-editor -- :10 vt10
```

Press Ctrl+Alt+F7 [noparse](or Ctrl+Alt+F8)[/noparse] to switch back to the GUI.

HTH

---

### Post by Azdour on 2011-05-16
Hi,

Thanks.

---

### Post by Azdour on 2011-05-17
Hi,

I have now played with your many suggestions :)

I believe that the blanking of the login screen is actually to do with the power management, so I ran:

```
sudo -u gdm dbus-launch gnome-screensaver-preferences

```

Click on the Power Management button and set the display to sleep as never and that did the trick.

Thanks for the help.

---

### Post by sisco311 on 2011-05-17
You're welcome!

---

### Post by Azdour on 2011-05-17
Hi,

Ok, that did not work. I came back after being away for sometime and the screen was blank...

---

### Post by Azdour on 2011-05-17
Hi,

Ok scrub that. It does work. Not sure what happened the first time but the login screen has no been one for 1.5 hours without turning off...

---

