---
title: "dbus-daemon is consuming memory"
date: 2010-05-04
forum: General Help
---

### Post by GlennW on 2010-05-04
Hi all,

I've just upgraded to 10.04. I love it. I've been running dark themes for a long time and this upgrade merged seamlessly with my setup. 

There is a nasty problem that I've noticed on only my desktop box (laptop is fine, also upgraded to 10.04). The dbus-daemon is hogging approximately 50% of my cpu cycles.

Is there a way to limit this? I'm watching this via the System Monitor and the % CPU. My laptop registers its dbus-daemon % CPU as 0.

Solutions?

Thanks.

---

### Post by GlennW on 2010-05-06
Well, it's gone from bad to worse. At this point, I've lost all the panel menus, super key functionality is gone, and Alt+F2 doesn't work either. 

The bizarre thing is that compiz is working. That's great but isn't worth a hill of beans if I can do nothing but spin the desktop. 

Every time I upgrade to a new distro something like this happens and I end up having to do a fresh install. 

If the upgrade doesn't work or is buggy then just say that I need to do complete install.

---

### Post by rnerwein on 2010-05-06
hi
for dbus-daemon have a look at the command line interface ( in a terminal type: man -k dbus - this will show you all the
commands and function calls wich are available for dbus [ for you i think only section 1 ( 1 ) is for interesting. )
try: dbus-monitor
and have a look at your /var/log logfiles ( messages, syslog etc. )
good luck
ciao

---

### Post by Ganton on 2010-11-21
Just in case it helps, you can see [http://art.ubuntuforums.org/showthread.php?t=1437780](http://art.ubuntuforums.org/showthread.php?t=1437780)

---

