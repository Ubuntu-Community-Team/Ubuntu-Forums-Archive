---
title: "Slow performance with some applications"
date: 2010-03-05
forum: General Help
---

### Post by richgriswold on 2010-03-05
I'm experiencing slow performance with several applications.  They take a long time to load, the file dialog takes several seconds to refresh when I change directories, the menus take several seconds to appear, and in general they are almost unusable.  This only seems to effect some applications, but not other applications.  A few of the effected applications include:

[LIST]
[*]Xiphos
[*]Gnucash
[*]Firefox
[*]Gthumb
[/LIST]

However many other applications, such as Google Chrome, Gimp, Inkscape, VirtualBox, Xine, Kmymoney, and so on work flawlessly.

I'm running Xubuntu 9.10 on a Compaq CQ60-420US, with 2GB RAM, a Pentium dual core T4200 2.0GHz, an 120GB free on the hard drive.  I've modified my installation to use XDM instead of GDM, and instead of using the XFCE session, I'm using Xmonad for a window manager.  Perhaps there's some service that these applications rely on that should be running and isn't.  Here's a list of the processes that are running when my session starts:

[LIST]
[*]/usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session sh /home/richard/.xsession
[*]/usr/bin/ssh-agent /usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session sh /home/richard/.xsession
[*]sh /home/richard/.xsession
[*]/usr/bin/dbus-launch --exit-with-session sh [*]/bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
[*]gnome-power-manager
[*]syndaemon -i 4 -d -t -K -R
[*]/home/richard/bin/xmonad-x86_64-linux
[*]/usr/lib/libgconf2-4/gconfd-2
[*]/usr/lib/notification-daemon/notification-daemon
[*]gnome-screensaver
[/LIST]

---

### Post by Daveski on 2010-03-05
Try System Monitor or top to see which what the memory footprint and CPU usage of the running processes are.

---

### Post by richgriswold on 2010-03-26
I tried checked memory and CPU usage, and everything looked okay.  There was plenty of available memory and no applications were hogging the CPU.

I finally stumbled on the fix yesterday - disabling IPv6.  When I disable IPv6 the performance of all applications is great.  When I enable IPv6, it's lousy.  I added the following to the end of /etc/sysctl.conf:

```
 net.ipv6.conf.all.disable_ipv6 = 1
```

I'm not sure why IPv6 would cause slow performance with the menus in an application like gthumb, so I'll probably dig into this further.  Hope this helps if anyone else is having this problem.

---

### Post by BigJules on 2010-04-22
Well dang my boots - this does fix the slows in my Karmic! Now I'm not one to complain about that, but what the **** has disabling ipv6 go to do with (e.g.) putting up a terminal, firing up gedit, using nautilus...?

---

