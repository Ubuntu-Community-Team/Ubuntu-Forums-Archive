---
title: "Update messed up my computer (again)"
date: 2011-05-26
forum: General Help
---

### Post by jesuisbenjamin on 2011-05-26
Hello there,

i just ran updates as usual, trusting Ubuntu repositories are fine. But as i started up my computer again it's completely messed up.
The log-in screen is blue, the interface is all squarish, everything changed and a black area replaces my dock.
What the hek just happened? i already had such an episode in 10.10 which messed up all my computer.
How can i remove whatever has been installed by this update and reinstall whatever has been remove?

Thanks.

Here is my var/log/apt/history.log:
```
Start-Date: 2011-05-26  11:06:36
Upgrade: policykit-1-gnome:i386 (0.99-1ubuntu4, 0.101-2ubuntu3~natty1), libqt4-opengl:i386 (4.7.2-0ubuntu6, 4.7.2-0ubuntu6.1), libpolkit-gobject-1-0:i386 (0.101-1ubuntu1, 0.101-4~natty1), telepathy-salut:i386 (0.4.0-1, 0.5.0-1~natty1), libqt4-declarative:i386 (4.7.2-0ubuntu6, 4.7.2-0ubuntu6.1), libtelepathy-glib0:i386 (0.14.3-1ubuntu1, 0.14.6-0ubuntu1~natty~build1), avahi-daemon:i386 (0.6.30-0ubuntu2, 0.6.30-3ubuntu1~natty1), cairo-dock-plug-ins-integration:i386 (2.3.1~0alpha0~20110506-0ubuntu1~ppa0~natty, 2.3.1~0alpha0~20110519-0ubuntu1~ppa0~natty), libavahi-common-data:i386 (0.6.30-0ubuntu2, 0.6.30-3ubuntu1~natty1), libqt4-test:i386 (4.7.2-0ubuntu6, 4.7.2-0ubuntu6.1), glib-networking:i386 (2.28.5-0ubuntu1, 2.28.6.1-0ubuntu1), libqt4-sql-mysql:i386 (4.7.2-0ubuntu6, 4.7.2-0ubuntu6.1), libqt4-dbus:i386 (4.7.2-0ubuntu6, 4.7.2-0ubuntu6.1), cairo-dock:i386 (2.3.1~0alpha0~20110506-0ubuntu1~ppa0~natty, 2.3.1~0alpha0~20110519-0ubuntu1~ppa0~natty), libibus2:i386 (1.3.9-0ubuntu3, 1.3.9-0ubuntu4~gtk3), ibus-gtk:i386 (1.3.9-0ubuntu3, 1.3.9-0ubuntu4~gtk3), gnome-menus:i386 (2.30.5-0ubuntu3, 3.0.0-0ubuntu1), libpam-gnome-keyring:i386 (2.92.92.is.2.32.1-0ubuntu2, 3.0.2-1~natty2), gir1.2-soup-2.4:i386 (2.34.0-0ubuntu1, 2.34.2-1~natty1), libtotem-plparser17:i386 (2.32.4-0ubuntu1, 2.32.4-3~natty1), libnotify4:i386 (0.7.2-0ubuntu2, 0.7.3-1~natty1), cairo-dock-plug-ins:i386 (2.3.1~0alpha0~20110506-0ubuntu1~ppa0~natty, 2.3.1~0alpha0~20110519-0ubuntu1~ppa0~natty), policykit-1:i386 (0.101-1ubuntu1, 0.101-4~natty1), libgnome-menu2:i386 (2.30.5-0ubuntu3, 3.0.0-0ubuntu1), libsoup2.4-1:i386 (2.34.0-0ubuntu1, 2.34.2-1~natty1), libmission-control-plugins0:i386 (5.7.7-1, 5.7.11-1~natty1), avahi-utils:i386 (0.6.30-0ubuntu2, 0.6.30-3ubuntu1~natty1), gsettings-desktop-schemas:i386 (3.0.0-0ubuntu1, 3.0.1-1~natty1), network-manager-gnome:i386 (0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1, 0.8.4~git.20110318t152954.9c4c9a0-0ubuntu1+noindicator1~build1), libgnome-bluetooth8:i386 (2.91.2.is.2.32.0-0ubuntu3, 3.0.0-1ubuntu1~natty1), cairo-dock-data:i386 (2.3.1~0alpha0~20110506-0ubuntu1~ppa0~natty, 2.3.1~0alpha0~20110519-0ubuntu1~ppa0~natty), libpolkit-gtk-1-0:i386 (0.99-1ubuntu4, 0.101-2ubuntu3~natty1), libgnomekbd-common:i386 (2.32.0-0ubuntu1, 3.0.0.1-1~natty1), libqt4-xmlpatterns:i386 (4.7.2-0ubuntu6, 4.7.2-0ubuntu6.1), gir1.2-freedesktop:i386 (0.10.7-0ubuntu1, 0.10.8-1ubuntu1~natty1), libqt4-help:i386 (4.7.2-0ubuntu6, 4.7.2-0ubuntu6.1), gnome-orca:i386 (3.0.0-0ubuntu2, 3.0.2-0ubuntu1~natty~build1), python-avahi:i386 (0.6.30-0ubuntu2, 0.6.30-3ubuntu1~natty1), libstartup-notification0:i386 (0.10-1build1, 0.12-1~natty1), libgdata11:i386 (0.8.0-0ubuntu1, 0.8.1-1~natty1), libgdu0:i386 (2.32.1-0ubuntu4, 3.0.0-1ubuntu1~natty1), cairo-dock-core:i386 (2.3.1~0alpha0~20110506-0ubuntu1~ppa0~natty, 2.3.1~0alpha0~20110519-0ubuntu1~ppa0~natty), libqtcore4:i386 (4.7.2-0ubuntu6, 4.7.2-0ubuntu6.1), libavahi-gobject0:i386 (0.6.30-0ubuntu2, 0.6.30-3ubuntu1~natty1), libegroupwise1.2-13:i386 (2.32.2-0ubuntu2, 3.0.0-1ubuntu1~natty1), gir1.2-glib-2.0:i386 (0.10.7-0ubuntu1, 0.10.8-1ubuntu1~natty1), libtelepathy-logger2:i386 (0.2.6-1ubuntu1, 0.2.9-1~natty1), telepathy-idle:i386 (0.1.8-1ubuntu1, 0.1.10-1~natty1), libgweather-common:i386 (2.30.3-1ubuntu1, 3.0.0-0ubuntu1~natty1), libecal1.2-8:i386 (2.32.2-0ubuntu2, 3.0.0-1ubuntu1~natty1), avahi-autoipd:i386 (0.6.30-0ubuntu2, 0.6.30-3ubuntu1~natty1), rdesktop:i386 (1.6.0-3ubuntu4, 1.6.0-3ubuntu4.1), libedataserver1.2-14:i386 (2.32.2-0ubuntu2, 3.0.0-1ubuntu1~natty1), vino:i386 (2.32.1-0ubuntu2.1, 3.0.2-0ubuntu4~natty1), mousetweaks:i386 (3.0.0-0ubuntu2, 3.0.2-0ubuntu1~natty~build2), gir1.2-notify-0.7:i386 (0.7.2-0ubuntu2, 0.7.3-1~natty1), telepathy-mission-control-5:i386 (5.7.7-1, 5.7.11-1~natty1), libqt4-sql:i386 (4.7.2-0ubuntu6, 4.7.2-0ubuntu6.1), telepathy-logger:i386 (0.2.6-1ubuntu1, 0.2.9-1~natty1), libqt4-svg:i386 (4.7.2-0ubuntu6, 4.7.2-0ubuntu6.1), telepathy-gabble:i386 (0.11.10-1ubuntu1, 0.12.0-1~natty1), libqt4-xml:i386 (4.7.2-0ubuntu6, 4.7.2-0ubuntu6.1), libsoup-gnome2.4-1:i386 (2.34.0-0ubuntu1, 2.34.2-1~natty1), libqt4-network:i386 (4.7.2-0ubuntu6, 4.7.2-0ubuntu6.1), libqt4-designer:i386 (4.7.2-0ubuntu6, 4.7.2-0ubuntu6.1), gnome-icon-theme:i386 (2.31.0-0ubuntu2, 3.0.0-1ubuntu1~natty1), libavahi-client3:i386 (0.6.30-0ubuntu2, 0.6.30-3ubuntu1~natty1), ibus:i386 (1.3.9-0ubuntu3, 1.3.9-0ubuntu4~gtk3), libqtgui4:i386 (4.7.2-0ubuntu6, 4.7.2-0ubuntu6.1), librsvg2-2:i386 (2.32.1-0ubuntu3, 2.34.0-0ubuntu2~natty2), libpolkit-backend-1-0:i386 (0.101-1ubuntu1, 0.101-4~natty1), libxklavier16:i386 (5.0-2ubuntu1, 5.1-1ubuntu1~natty1), python-gmenu:i386 (2.30.5-0ubuntu3, 3.0.0-0ubuntu1), libavahi-glib1:i386 (0.6.30-0ubuntu2, 0.6.30-3ubuntu1~natty1), telepathy-butterfly:i386 (0.5.15-1, 0.5.15-2.1~natty1), yelp-xsl:i386 (3.0.0-0ubuntu1, 3.0.2-1~natty1), libqt4-script:i386 (4.7.2-0ubuntu6, 4.7.2-0ubuntu6.1), cairo-dock-plug-ins-data:i386 (2.3.1~0alpha0~20110506-0ubuntu1~ppa0~natty, 2.3.1~0alpha0~20110519-0ubuntu1~ppa0~natty), libnautilus-extension1:i386 (2.32.2.1-0ubuntu13, 3.0.2-0ubuntu1~natty1), libqt4-scripttools:i386 (4.7.2-0ubuntu6, 4.7.2-0ubuntu6.1), libavahi-common3:i386 (0.6.30-0ubuntu2, 0.6.30-3ubuntu1~natty1), python-ibus:i386 (1.3.9-0ubuntu3, 1.3.9-0ubuntu4~gtk3), binutils:i386 (2.21.0.20110327-2ubuntu2, 2.21.0.20110327-2ubuntu3), libavahi-ui0:i386 (0.6.30-0ubuntu2, 0.6.30-3ubuntu1~natty1), librsvg2-common:i386 (2.32.1-0ubuntu3, 2.34.0-0ubuntu2~natty2), libavahi-core7:i386 (0.6.30-0ubuntu2, 0.6.30-3ubuntu1~natty1), libpolkit-agent-1-0:i386 (0.101-1ubuntu1, 0.101-4~natty1), libgdata-common:i386 (0.8.0-0ubuntu1, 0.8.1-1~natty1)
End-Date: 2011-05-26  11:09:41
```

---

### Post by jesuisbenjamin on 2011-05-26
Wow. I just realised the entire Preferences > Appearance menu has disappeared! :s What in the world has happened?
Seriously i can't work on this thing. Please help.

PS: i am trying to back up my data, but i can't burn to CD because it does not read the full free space (only 137MB of 700MB, real new blank CD-Rs).

---

### Post by jesuisbenjamin on 2011-05-26
I reinstalled Ubuntu and i am so massively _pissed off_.

---

