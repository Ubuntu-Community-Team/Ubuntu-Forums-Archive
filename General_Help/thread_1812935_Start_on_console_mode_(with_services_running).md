---
title: "Start on console mode (with services running)"
date: 2011-07-27
forum: General Help
---

### Post by jorgecachoh on 2011-07-27
Hi,

I'm using a PC as a webserver so I'd like to:

 - Start it on console mode (it would be great to have a command to start GUI interface, just in case)

 - Have all services (networking, Apache, FTP, etc ...) running, althought there is no user logged in.

Is that possible?

Thanks!

        Jorge

---

### Post by sisco311 on 2011-07-27
Of course it is. You have to disable GDM. If you are useing Ubuntu 11.04 (natty), then check out: [http://ubuntuforums.org/showpost.php?p=10798400&postcount=4](http://ubuntuforums.org/showpost.php?p=10798400&postcount=4)

If you are useing an earlier version, then: [http://ubuntuforums.org/showthread.php?p=9644518#post9644518](http://ubuntuforums.org/showthread.php?p=9644518#post9644518)

---

### Post by jorgecachoh on 2011-07-27
Thanks sisco311,

I'm afraid I'm using a customized version of Ubuntu 10.10 (it is a Efika MX Smarttop) and I don't have /etc/default/grub file ;-(

Thanks anyway

         Jorge

---

### Post by sisco311 on 2011-07-27
> **jorgecachoh said:**
> Thanks sisco311,

I'm afraid I'm using a customized version of Ubuntu 10.10 (it is a Efika MX Smarttop) and I don't have /etc/default/grub file ;-(

Thanks anyway

         Jorge

That probably means that you are using grub legacy. The **text** parameter should work, but you have to edit /boot/grub/menu.lst. See:
[uhelp]/community/GrubHowto#Setting kernel parameters[/uhelp]

---

### Post by jorgecachoh on 2011-07-27
I don't have neither a /boot/grub/menu.lst file ;-(

---

### Post by sisco311 on 2011-07-27
It seams it's using u-boot. I have no clue how to pass the text kernel parameter in u-boot. You may want to check the documentation: [http://www.denx.de/wiki/DULG/Manual](http://www.denx.de/wiki/DULG/Manual)

---

### Post by sisco311 on 2011-07-27
Alternatively you can comment out the **start on** stanza in /etc/init/gdm.conf. But you may have to repeat this each time GDM is upgraded. 

You can comment out a line by putting a # at the beginning:
```
# gdm - GNOME Display Manager
#
# The display manager service manages the X servers running on the
# system, providing login and auto-login services

description     "GNOME Display Manager"
author          "William Jon McCann <mccann@jhu.edu>"

**#**start on ((filesystem
**#**            and (runlevel [!06]
**#**            and (started dbus
**#**            and (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
**#**            or  (graphics-device-added PRIMARY_DEVICE_FOR_DISPLAY=1
**#**            or   stopped udev-fallback-graphics)))))
**#**            or  runlevel PREVLEVEL=S)

stop on runlevel [016]

```

---

