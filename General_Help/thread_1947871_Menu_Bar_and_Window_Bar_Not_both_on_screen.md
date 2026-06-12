---
title: "Menu Bar and Window Bar Not both on screen"
date: 2012-03-27
forum: General Help
---

### Post by shaviro on 2012-03-27
Today I installed the latest new Linux kernel (3.0.0-17 generic) and when I rebooted my desktop had changed. I am no longer able to view both the Menu Bar at the top and the Window Bar at the bottom. I have to move up or down with the mouse to see either of them; the other is always offscreen. (I am using the Gnome Classic interface on top of Ubuntu 11.10). How can I restore the old condition, where I could see both bars at the top and bottom of the screen?

---

### Post by bogan on 2012-04-06
Hi!, **shaviro**,

I have a similar setup to yours, only that I am also running Unity 2D Launcher.

I updated to 3.0.0-17 at the same time and had no problems, even the nvidia driver did not need reinstalling.

I can not offer any solutions, but are all your Gnome extensions still running??

Try:```
 sudo ps -ax | grep gnome
```Which should show all of these, at least:```
alan@alan-MS-7616:~$ ps -ax | grep gnome
Warning: bad ps syntax, perhaps a bogus '-'? See http://procps.sf.net/faq.html
 1496 ?        Sl     0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
 1505 ?        Ssl    0:00 /usr/bin/gnome-session --session=gnome-classic
 1538 ?        Ss     0:00 /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session
 /usr/bin/gnome-session --session=gnome-classic
 1541 ?        S      0:00 /usr/bin/dbus-launch --exit-with-session
 /usr/bin/gnome-session --session=gnome-classic
 1562 ?        Sl     0:00 /usr/lib/gnome-settings-daemon/gnome-settings-daemon
 1573 ?        Sl     0:00 /usr/lib/gnome-settings-daemon/gsd-printer
 1583 ?        Sl     0:02 gnome-panel
 1593 ?        Sl     0:00 gnome-sound-applet
 1595 ?        Sl     0:00 /usr/lib/gnome-settings-daemon/gnome-fallback-mount-helper
 1598 ?        Sl     0:00 /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
 1695 ?        S      0:00 /usr/lib/gnome-disk-utility/gdu-notification-daemon
 2039 ?        Sl     0:00 gnome-terminal
 2044 ?        S      0:00 gnome-pty-helper
 2100 pts/0    S+     0:00 grep --color=auto gnome
alan@alan-MS-7616:~$ 
```[ The '0:00' or '0:02' digits may be different, they show the current CPU usage].

Otherwise I suggest you check the settings in CCSM.

Chao!, bogan.

---

