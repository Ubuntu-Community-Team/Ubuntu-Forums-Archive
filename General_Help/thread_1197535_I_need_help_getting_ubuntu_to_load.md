---
title: "I need help getting ubuntu to load"
date: 2009-06-26
forum: General Help
---

### Post by politico34 on 2009-06-26
I am running 9.04. It only loads the desktop wallpaper and the "working" mouse cursor. When I ran recovery mode and pushed ctl+alt+f1 I saw this error at the bottom of a bunch of text


[COLOR="Red"]Starting avahi mDNS/DNS-SD Daemon avahi-daemon
Timeout reached wating for return value
Could not receive return value from daemon process[/COLOR]

Please Help, I miss ubuntu.

---

### Post by clonne4crw on 2009-06-26
Whatever the hell it is, its oviously a problem.
Heres what I would do:
*get to a terminal
boot recovery mode or ctrl-alt-f2 or something.
*install syssv-rc-conf:
$ sudo apt-get isntall sysv-rc-conf
run it
# sysv-rc-conf
and look around for the process that is being annoying.
use space to select/deselect, q to quit. reboot and see if it works.

---

### Post by siryuhan on 2009-06-26
Odd. Avahi is a networking daemon. Can you try to chmod -x /etc/init.d/avahi-daemon and see if that helps?

---

