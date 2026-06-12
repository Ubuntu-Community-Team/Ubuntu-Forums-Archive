---
title: "udev_monitor_new_from_netlink: error getting socket: Invalid Argument"
date: 2010-07-02
forum: General Help
---

### Post by sdowney717 on 2010-07-02
[http://superuser.com/questions/142165/ubuntu-upgrade-to-10-04-general-error-mounting-filesystems/142178](http://superuser.com/questions/142165/ubuntu-upgrade-to-10-04-general-error-mounting-filesystems/142178)
had this exact bug, ended up doing a reinstall of the LUCID OS to fix.
Parent's box was upgraded from Hardy to Lucid and it worked until yesterday.
In future, does anyone know how to fix it?

> ureadahead terminated with status 5.
udev_monitor_new_from_netlink: error getting socket: Invalid Argument
mountall:mountall.c:3204 assertion failed in main: udev_monitor = udev_monitor_new_from_netlink(udev,"udev")
init: mountall main process (2532) killed by ABRT signal.
General error mounting filesystems


---

### Post by dino99 on 2010-07-02
i often found that old config settings are a real nightmare on dist-upgrading

so clean the system: gconf-cleaner (yes to all), gtkorphan, bleachbit (as admin, set the prefs with care)

open all the related gnome folder (mostly hidden: gconf*, gnome2) and remove all the files  prior 2009 (or rename them first before deleting if you care)

sudo dpkg --configure -a

---

### Post by philinux on 2010-07-02
It could be this.
[http://ubuntuforums.org/showthread.php?t=1485990](http://ubuntuforums.org/showthread.php?t=1485990) post #5

Upgrade 8.04 -> 10.04 can break apt-get
[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

---

