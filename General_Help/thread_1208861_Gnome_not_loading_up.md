---
title: "Gnome not loading up"
date: 2009-07-09
forum: General Help
---

### Post by Intrepid Ibex on 2009-07-09
I did some configuring and when I decided to boot, Gnome somehow fails to load.

All I can see is my mouse and my desktop, no bars, no icons, no nothing.

Alt+f2 or right clicking the desktop won't work either.

---

### Post by wojox on 2009-07-09
Did you configure /etc/X11/xorg.conf?
Did you make a back up?
Look in there and see if there is a backup file.

---

### Post by Intrepid Ibex on 2009-07-10
No I didn't.

**E:** When launching ```
gnome-session
``` manually, I get a pop-up: ```
Could not acquire name on session bus
``` and terminal says: ```
[det@myhost ~]$ gnome-session
gnome-session[4552]: WARNING: Could not parse desktop file /home/det/.config/autostart/xfconf-migration-4.6.desktop: Key file does not have key 'Name'
gnome-session[4552]: WARNING: could not read /home/det/.config/autostart/xfconf-migration-4.6.desktop
GNOME_KEYRING_SOCKET=/tmp/keyring-32mWEY/socket
SSH_AUTH_SOCK=/tmp/keyring-32mWEY/socket.ssh

** (gnome-settings-daemon:4559): WARNING **: Failed to acquire org.gnome.SettingsDaemon

** (gnome-settings-daemon:4559): WARNING **: Could not acquire name

MCS->Xfconf settings migration complete

  

```

---

