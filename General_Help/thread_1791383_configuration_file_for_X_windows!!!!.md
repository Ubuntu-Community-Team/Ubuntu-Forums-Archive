---
title: "configuration file for X windows!!!!"
date: 2011-06-26
forum: General Help
---

### Post by Dlinux123 on 2011-06-26
Hi there, I am new to Linux. For an assignment in school we were supposed to access the configuration file for X - Window, in particular change the screen resolution. According to my Comp TIA Linux + book we are supposed to use:  gedit /etc/X11/xorg.conf .  All it does is open a blank document named xorg.conf, I checked the spelling, I used my graphical interface to route to /etc then I opened X11, but there is no xorg .conf. any help would be appreciated. by the way I have installed a recent updates as well.

---

### Post by nzjethro on 2011-06-26
By default, there is no xorg.conf in Ubuntu 10.04 or higher. You can create one, or else there are a number of system config files in the directory:

```
/usr/share/X11/xorg.conf.d/
```

Maybe check them out, and try to find one that corresponds to your monitor.

---

### Post by deserthowler on 2011-06-26
The easiest way to get an xorg.conf for me ... I got an old Ubuntu book from the public library and used the live CD to get get an xorg.conf file.  I'm not very sure that any modern distro has xorg.conf file.

Earl

---

