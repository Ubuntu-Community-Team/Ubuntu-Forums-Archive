---
title: "Gnome does not start on login"
date: 2009-12-20
forum: General Help
---

### Post by H13N.H3N on 2009-12-20
well, i was going to solve this by my own but that way i always end breaking my system.
I'm working on Ubuntu Studio 9.10 Karmic Koala with Gnome, is nearly as in it first installation state as i removed only PA from my system. today i installed 'xserver-xorg-input-joystick' package, i did it from the terminal with 'sudo apt-get install xserver-xorg-input-joystick', the package demanded uninstall some phyton dependencies which i didn't recognize as an important thread so i just pressed 'y' to proceed with the installation, i restarted my system and the desktop folders didn't show up, nor the panels but the background picture did. What i did next was login again restarting my pc taking in count that could be a random stuck with gnome like it happen some weeks ago, really unusual but happens, after realize that gnome wouldn't start once again i loged again but changed the desktop environment to 'xterm' which has a terminal that led me start 'gnome-panel', 'metacity' and 'nautilus', this led me have my gnome enviorement working again, no apps or configuration are lost, i can say that it work as flawless as always which is good. i must say that before install 'xserver-xorg-input-joystick' i installed 'Software-Center' that is the new remove/install software manager in the regular distrubution, also updated my system, i must say also that after installed them i restarted my system and nothing went wrong so i'm sure that 'xserver-xorg-input-joystick' had something to do, i looked at '.bash_history' to see if somehow the lines which shown which dependencies would be uninstalled were there, no luck. fortunately i find them in 'Log File Viewer' under two sections, the first and merely obvious was 'Aptitude':
```
Aptitude 0.4.11.11: log report
Sun, Dec 20 2009 16:18:11 -0600

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 1 packages, and remove 7 packages.
9,822kB of disk space will be freed
===============================================================================
[REMOVE, NOT USED] libvala0
[REMOVE, NOT USED] python-alsaaudio
[REMOVE, NOT USED] python-compizconfig
[REMOVE, NOT USED] python-dateutil
[REMOVE, NOT USED] python-feedparser
[REMOVE, NOT USED] python-sqlalchemy
[REMOVE, NOT USED] valac
[INSTALL] xserver-xorg-input-joystick
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Sun, Dec 20 2009 16:31:39 -0600

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
```
and the second was more descriptive but also long:
```

2009-12-20 16:18:41 remove valac 0.7.6-1ubuntu1 0.7.6-1ubuntu1
2009-12-20 16:18:41 status half-configured valac 0.7.6-1ubuntu1
2009-12-20 16:18:41 status half-installed valac 0.7.6-1ubuntu1
2009-12-20 16:18:41 status triggers-pending man-db 2.5.6-2
2009-12-20 16:18:41 status half-installed valac 0.7.6-1ubuntu1
2009-12-20 16:18:41 status config-files valac 0.7.6-1ubuntu1
2009-12-20 16:18:41 status config-files valac 0.7.6-1ubuntu1
2009-12-20 16:18:41 status config-files valac 0.7.6-1ubuntu1
2009-12-20 16:18:41 status config-files valac 0.7.6-1ubuntu1
2009-12-20 16:18:41 status not-installed valac <none>
2009-12-20 16:18:41 status installed libvala0 0.7.6-1ubuntu1
2009-12-20 16:18:41 remove libvala0 0.7.6-1ubuntu1 0.7.6-1ubuntu1
2009-12-20 16:18:41 status half-configured libvala0 0.7.6-1ubuntu1
2009-12-20 16:18:41 status half-installed libvala0 0.7.6-1ubuntu1
2009-12-20 16:18:42 status triggers-pending libc-bin 2.10.1-0ubuntu15
2009-12-20 16:18:42 status config-files libvala0 0.7.6-1ubuntu1
2009-12-20 16:18:42 status config-files libvala0 0.7.6-1ubuntu1
2009-12-20 16:18:42 status installed python-alsaaudio 0.2-1ubuntu2
2009-12-20 16:18:42 remove python-alsaaudio 0.2-1ubuntu2 0.2-1ubuntu2
2009-12-20 16:18:42 status half-configured python-alsaaudio 0.2-1ubuntu2
2009-12-20 16:18:44 status triggers-pending python-support 1.0.3ubuntu1
2009-12-20 16:18:44 status half-installed python-alsaaudio 0.2-1ubuntu2
2009-12-20 16:18:45 status config-files python-alsaaudio 0.2-1ubuntu2
2009-12-20 16:18:45 status config-files python-alsaaudio 0.2-1ubuntu2
2009-12-20 16:18:45 status config-files python-alsaaudio 0.2-1ubuntu2
2009-12-20 16:18:45 status not-installed python-alsaaudio <none>
2009-12-20 16:18:45 status installed python-compizconfig 0.8.2-0ubuntu1
2009-12-20 16:18:46 remove python-compizconfig 0.8.2-0ubuntu1 0.8.2-0ubuntu1
2009-12-20 16:18:46 status half-configured python-compizconfig 0.8.2-0ubuntu1
2009-12-20 16:18:46 status half-installed python-compizconfig 0.8.2-0ubuntu1
2009-12-20 16:18:46 status config-files python-compizconfig 0.8.2-0ubuntu1
2009-12-20 16:18:46 status config-files python-compizconfig 0.8.2-0ubuntu1
2009-12-20 16:18:46 status config-files python-compizconfig 0.8.2-0ubuntu1
2009-12-20 16:18:46 status not-installed python-compizconfig <none>
2009-12-20 16:18:46 status installed python-dateutil 1.4.1-3
2009-12-20 16:18:46 remove python-dateutil 1.4.1-3 1.4.1-3
2009-12-20 16:18:46 status half-configured python-dateutil 1.4.1-3
2009-12-20 16:18:47 status half-installed python-dateutil 1.4.1-3
2009-12-20 16:18:47 status config-files python-dateutil 1.4.1-3
2009-12-20 16:18:47 status config-files python-dateutil 1.4.1-3
2009-12-20 16:18:47 status config-files python-dateutil 1.4.1-3
2009-12-20 16:18:47 status not-installed python-dateutil <none>
2009-12-20 16:18:47 status installed python-feedparser 4.1-14
2009-12-20 16:18:47 remove python-feedparser 4.1-14 4.1-14
2009-12-20 16:18:47 status half-configured python-feedparser 4.1-14
2009-12-20 16:18:47 status half-installed python-feedparser 4.1-14
2009-12-20 16:18:47 status config-files python-feedparser 4.1-14
2009-12-20 16:18:47 status config-files python-feedparser 4.1-14
2009-12-20 16:18:47 status config-files python-feedparser 4.1-14
2009-12-20 16:18:47 status not-installed python-feedparser <none>
2009-12-20 16:18:47 status installed python-sqlalchemy 0.5.5-1
2009-12-20 16:18:48 remove python-sqlalchemy 0.5.5-1 0.5.5-1
2009-12-20 16:18:48 status half-configured python-sqlalchemy 0.5.5-1
2009-12-20 16:18:48 status half-installed python-sqlalchemy 0.5.5-1
2009-12-20 16:18:48 status config-files python-sqlalchemy 0.5.5-1
2009-12-20 16:18:48 status config-files python-sqlalchemy 0.5.5-1
2009-12-20 16:18:48 status config-files python-sqlalchemy 0.5.5-1
2009-12-20 16:18:48 status not-installed python-sqlalchemy <none>
2009-12-20 16:18:48 trigproc man-db 2.5.6-2 2.5.6-2
2009-12-20 16:18:48 status half-configured man-db 2.5.6-2
2009-12-20 16:18:49 status installed man-db 2.5.6-2
2009-12-20 16:18:49 trigproc libc-bin 2.10.1-0ubuntu15 2.10.1-0ubuntu15
2009-12-20 16:18:49 status half-configured libc-bin 2.10.1-0ubuntu15
2009-12-20 16:18:50 status installed libc-bin 2.10.1-0ubuntu15
2009-12-20 16:18:50 trigproc python-support 1.0.3ubuntu1 1.0.3ubuntu1
2009-12-20 16:18:50 status half-configured python-support 1.0.3ubuntu1
2009-12-20 16:18:52 status installed python-support 1.0.3ubuntu1
2009-12-20 16:18:53 startup archives unpack
2009-12-20 16:18:55 install xserver-xorg-input-joystick <none> 1:1.4.0-0ubuntu1
2009-12-20 16:18:55 status half-installed xserver-xorg-input-joystick 1:1.4.0-0ubuntu1
2009-12-20 16:18:55 status triggers-pending hal 0.5.13-1ubuntu8
2009-12-20 16:18:55 status half-installed xserver-xorg-input-joystick 1:1.4.0-0ubuntu1
2009-12-20 16:18:55 status triggers-pending man-db 2.5.6-2
2009-12-20 16:18:55 status half-installed xserver-xorg-input-joystick 1:1.4.0-0ubuntu1
2009-12-20 16:18:55 status unpacked xserver-xorg-input-joystick 1:1.4.0-0ubuntu1
2009-12-20 16:18:55 status unpacked xserver-xorg-input-joystick 1:1.4.0-0ubuntu1
2009-12-20 16:18:55 trigproc hal 0.5.13-1ubuntu8 0.5.13-1ubuntu8
2009-12-20 16:18:55 status half-configured hal 0.5.13-1ubuntu8
2009-12-20 16:18:55 status installed hal 0.5.13-1ubuntu8
2009-12-20 16:18:55 trigproc man-db 2.5.6-2 2.5.6-2
2009-12-20 16:18:55 status half-configured man-db 2.5.6-2
2009-12-20 16:18:56 status installed man-db 2.5.6-2
2009-12-20 16:18:57 startup packages configure
2009-12-20 16:18:57 configure xserver-xorg-input-joystick 1:1.4.0-0ubuntu1 1:1.4.0-0ubuntu1
2009-12-20 16:18:57 status unpacked xserver-xorg-input-joystick 1:1.4.0-0ubuntu1
2009-12-20 16:18:57 status half-configured xserver-xorg-input-joystick 1:1.4.0-0ubuntu1
2009-12-20 16:18:57 status installed xserver-xorg-input-joystick 1:1.4.0-0ubuntu1
2009-12-20 17:19:44 startup archives unpack
```

this was on 'dpkg.log'. Taking this in count i uninstalled 'xserver-xorg-input-joystick 1:1.4.0-0ubuntu1' and re-installed those packages from the Synaptic Package Manager, of course in the process i read what were the use of each one, then restarted my system and no luck, looking at this situation i installed once again 'xserver-xorg-input-joystick 1:1.4.0-0ubuntu1' as having it uninstalled was or is quite the same, it's just courious that this time, installed from the Synaptic Package Manager, did not demanded any other of the anterior packages have to be uninstalled. my thoughs are directed in a configuration file but perhaps i made enough by myself for now and i wouldn't like to ruin my current instalation of gnome as i have it working perfectly smooth, at least is problem of the graphical desktop which is not vital at all, maybe i will work with KDE or Enlightment while i find a solution for this, any help would be very apreciated.

greetings

---

### Post by H13N.H3N on 2009-12-22
never mind, i'll stick with xcfe desktop enviorement, it's just awsome and perfect for heavy work =)

---

