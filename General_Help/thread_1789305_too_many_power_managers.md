---
title: "too many power managers"
date: 2011-06-23
forum: General Help
---

### Post by pratikk on 2011-06-23
Following a discussion on the Asus forum on overheating, ([http://ubuntuforums.org/showthread.php?t=1768551&page=4](http://ubuntuforums.org/showthread.php?t=1768551&page=4)), I find that my netbook is running three power managers simultaneously: gnome, xfce and jupiter. How do I disable (not uninstall) these one by one, so that I can identify the most efficient manager by elimination?

Back story: my observation posted in the Asus forum was that Lucid runs several degrees hotter than XP on my 1005HA machine, which is a dual boot. 

Thanks

Pratik

EEEPC 1005HA, Lucid 10.04, XFCE4 desktop

---

### Post by ajgreeny on 2011-06-23
You can either find the system that makes them start at boot time, and I have no idea what that is in xfce (xubuntu?), or if that is not so simple just remove the execute permission from the ones you don't want to run temporarily by using the command ```
sudo chmod -x /usr/bin/gnome-power-manager
```etc etc.

However, there must be a list of startup applications somewhere more easily found, I'm sure.

There is a similar problem in Lubuntu (lxde) which by deafult runs gnome-power-manager.  However I can not get that to work to suspend my netbook so added xfce4-power-manager as well, which does work properly, but it means I have to remove the gnome version from the startup applications and add the xfce4 version.  It's not too difficult, but in lxde involves manually editing a text config file /etc/xdg/lxsession/Lubuntu/autostart.  Perhaps there is a similar file in xfce.

---

### Post by LordNeo on 2011-06-23
Check in the startup apps and disable those you find.

Also check this link about how to control services started at boot:

[http://blog.ubuntu-tweak.com/2007/09/30/how-to-control-ubuntus-services-easily.html](http://blog.ubuntu-tweak.com/2007/09/30/how-to-control-ubuntus-services-easily.html)

---

### Post by Jouke74 on 2011-06-23
For certain Gnome Power manager and Jupiter are complementary, not interfering with each other. Be careful to uninstall all of them. E.g. Gnome power manager arranges the screen dimming, shutdown of screen after x amount of time and battery status etc. While jupiter arranges the cpu scaling, turning off peripheral devices and different FSB profiles. If you uninstall either one, these functions will be lost. 

XFCE power manager is maybe double, but if you are using XFCE instead of Gnome this manager takes over the Gnome power manager part. All these issues are likely not going to solve your overheating. The configuration of the laptop mode maybe. I would strongly suggest to try adding "acpi_osi=Linux" to grub default, and reverting to an older kernel until this bug is fixed.

---

### Post by pratikk on 2011-06-24
Thank you, everyone. Each of you has given me a starting point which should get me somewhere. Will try them out as soon as I finish work.

Pratik

---

