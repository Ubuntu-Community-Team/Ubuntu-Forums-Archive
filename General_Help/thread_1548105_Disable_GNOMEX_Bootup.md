---
title: "Disable GNOME/X Bootup"
date: 2010-08-07
forum: General Help
---

### Post by itsmilesdavis on 2010-08-07
I do not want gnome to start automatically when the machine boots up.  I want to boot to a console and use startx as needed.

After googling, I tried:
```
update-rc.d -f gdm remove
```
This did not work.  So, I also installed rcconf and unchecked x11-console and verified gdm was unchecked.  System STILL loads gnome.  I'm at a loss.  Any suggestions?

---

### Post by chopinhauer on 2010-08-07
> **itsmilesdavis said:**
> This did not work.  So, I also installed rcconf and unchecked x11-console and verified gdm was unchecked.  System STILL loads gnome.  I'm at a loss.  Any suggestions?

That is because Ubuntu doesn't use System V init files for startup any more, it uses a program called Upstart. You have to edit the file /etc/init/gdm.conf and comment the 'start' line to obtain something like:
```

#start on (filesystem
#          and started dbus
#          and (graphics-device-added fb0 PRIMARY_DEVICE_FOR_DISPLAY=1
#               or drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
#               or stopped udevtrigger))
stop on runlevel [016]

```

---

### Post by itsmilesdavis on 2010-08-07
Thanks!  That fixed it.

Should I go back in rcconf and enable gdm and x11-console?  Or, leave them off?

---

### Post by chopinhauer on 2010-08-07
> **itsmilesdavis said:**
> 
Should I go back in rcconf and enable gdm and x11-console?  Or, leave them off?


It doesn't matter, the gdm rc script just prints a message:
```

$ /etc/init.d/gdm start
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service gdm start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start gdm

```

---

