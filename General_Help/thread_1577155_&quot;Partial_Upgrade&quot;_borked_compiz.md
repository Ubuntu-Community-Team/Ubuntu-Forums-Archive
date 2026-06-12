---
title: "&quot;Partial Upgrade&quot; borked compiz"
date: 2010-09-18
forum: General Help
---

### Post by MeisBarry on 2010-09-18
Ubuntu 10.04 x64.

This past week Update Manager came up and offered to do a partial upgrade, as some packages could not be upgraded.  I had just assumed the 'partial' was an issue with Opera (as I have seen in the past), so I allowed it and let the update go through.

This morning when I turned on the system, Metacity is running, and Compiz is not.  My first thought was that the update somehow changed my defaults, so I went to change them back.  Desktop Effects could not be enabled through the menu (there was a screen flicker, then a "Desktop effects cannot be enabled" error).  

Running compiz from the terminal does this:

```
barry@Independence:~$ compiz --replace
compiz (core) - Fatal: Root visual is not a GL visual
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

Launching fallback window manager
```

Various other methods I found on the forums to fix it left me in the same state.  Clearly there's some issue that is preventing compositing or some other effect from working that Compiz needs.

I've never had to troubleshoot an update before, so I'm not sure where to look to see what exactly was changed. Can anyone give me some insight?

---

### Post by MeisBarry on 2010-09-18
I found the log.

```
Start-Date: 2010-09-17  22:57:15
Install: ubuntu-desktop (1.197), wine1.3-gecko (1.1.0-0ubuntu1~lucidppa1), libgl1-mesa-glx (7.7.1-1ubuntu3)
Upgrade: libsmbclient (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2), apt-transport-https (0.7.25.3ubuntu9.1, 0.7.25.3ubuntu9.3), libqt4-qt3support (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1), smbclient (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2), linux-image-2.6.32-24-generic (2.6.32-24.42, 2.6.32-24.43), wine1.3 (1.3.1-0ubuntu1, 1.3.2-0ubuntu1~lucidppa2), libqt4-script (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1), libqt4-designer (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1), libqt4-network (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1), libqt4-dbus (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1), empathy-common (2.30.2-0ubuntu1, 2.30.3-0ubuntu1), gnome-terminal (2.29.6-0ubuntu5, 2.30.2-0ubuntu1), python-software-properties (0.75.10, 0.75.10.1), libwbclient0 (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2), opera (10.61.6430, 10.62.6438), empathy (2.30.2-0ubuntu1, 2.30.3-0ubuntu1), linux-headers-2.6.32-24-generic (2.6.32-24.42, 2.6.32-24.43), firefox-branding (3.6.8+build1+nobinonly-0ubuntu0.10.04.1, 3.6.10+build1+nobinonly-0ubuntu0.10.04.1), apt-utils (0.7.25.3ubuntu9.1, 0.7.25.3ubuntu9.3), samba-common (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2), apt (0.7.25.3ubuntu9.1, 0.7.25.3ubuntu9.3), firefox (3.6.8+build1+nobinonly-0ubuntu0.10.04.1, 3.6.10+build1+nobinonly-0ubuntu0.10.04.1), linux-headers-2.6.32-24 (2.6.32-24.42, 2.6.32-24.43), winetricks (0.0+20100822-0ubuntu1, 0.0+20100904-0ubuntu1~lucidppa1), libqtcore4 (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1), sudo (1.7.2p1-1ubuntu5.1, 1.7.2p1-1ubuntu5.2), xulrunner-1.9.2 (1.9.2.8+build1+nobinonly-0ubuntu0.10.04.1, 1.9.2.10+build1+nobinonly-0ubuntu0.10.04.1), software-properties-gtk (0.75.10, 0.75.10.1), dpkg (1.15.5.6ubuntu4.1, 1.15.5.6ubuntu4.2), gnome-terminal-data (2.29.6-0ubuntu5, 2.30.2-0ubuntu1), google-chrome-stable (6.0.472.53-r57914, 6.0.472.62-r59676), libqt4-sql (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1), wine (1.2-0ubuntu1~lucidppa1, 1.2-1ubuntu1~lucidppa1), dpkg-dev (1.15.5.6ubuntu4.1, 1.15.5.6ubuntu4.2), gwibber-service (2.30.2-0ubuntu1, 2.30.2-0ubuntu2), libqt4-xml (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1), libqtgui4 (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1), samba-common-bin (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2), libqt4-sql-mysql (4.6.2-0ubuntu5, 4.6.2-0ubuntu5.1), winbind (3.4.7~dfsg-1ubuntu3.1, 3.4.7~dfsg-1ubuntu3.2), gwibber (2.30.2-0ubuntu1, 2.30.2-0ubuntu2), mountall (2.15.1, 2.15.2), firefox-gnome-support (3.6.8+build1+nobinonly-0ubuntu0.10.04.1, 3.6.10+build1+nobinonly-0ubuntu0.10.04.1), nautilus-sendto-empathy (2.30.2-0ubuntu1, 2.30.3-0ubuntu1), ttf-symbol-replacement-wine1.3 (1.3.1-0ubuntu1, 1.3.2-0ubuntu1~lucidppa2), lftp (4.0.2-1, 4.0.2-1ubuntu0.1)
Remove: libgl1-mesa-swx11 (7.7.1-1ubuntu3), wine1.2-gecko (1.0.0-0ubuntu4)
End-Date: 2010-09-17  22:59:52

Start-Date: 2010-09-17  23:00:26
Remove: libqt3-headers (3.3.8-b-6ubuntu2), libosmesa6 (7.7.1-1ubuntu3), libqt3-compat-headers (3.3.8-b-6ubuntu2), qt3-dev-tools (3.3.8-b-6ubuntu2), freeglut3 (2.6.0-0ubuntu2)
End-Date: 2010-09-17  23:00:31
```

---

### Post by MeisBarry on 2010-09-18
Solved.  The update somehow messed up my very frail ATI drivers :P

---

