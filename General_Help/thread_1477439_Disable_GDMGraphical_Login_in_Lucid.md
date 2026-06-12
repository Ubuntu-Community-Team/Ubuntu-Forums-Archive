---
title: "Disable GDM/Graphical Login in Lucid"
date: 2010-05-08
forum: General Help
---

### Post by BigRedd on 2010-05-08
Howdy,

       I've spent a good 3 hours or so hunting around for a solution to this, but most of what I've found are similar questions with no good solutions. It used to be that this was a service that could just be disabled in System>Preferences>Startup Services, but this is no longer the case it seems. I've tried tinkering with the runlevels in gdm.conf, but haven't had any success with it so far. I've tried commenting out the startup code in the gdm.conf as well. Also no luck.

Most of what I've found are older guides for Karmic and earlier, so if anyone has a more up-to-date solution for how to disable the gdm so I can auto-login to a terminal in Lucid, help me out here, haha.


cheers.

---

### Post by mkvnmtr on 2010-05-08
I did a minimal xfce4 10.04 install and I think it was installed so I just uninstalled it. Nothing bad happened. On a regular ubuntu I do not know. In synaptic choose it for uninstallation and see what it wants to take with it. If it is nothing important try it.

---

### Post by BigRedd on 2010-05-08
Good suggestion. It worked for the most part. I get a window with some options after boot, one of which is to go to a login terminal. It's progress. I'll tinker around and see if I can just get it to go straight to the login terminal from here.

Thanks for the reply! Very helpful.

---

### Post by recyclebin on 2010-05-10
You could try renaming /etc/init/gdm.conf to something like /etc/init/gdm.conf.bak and rebooting.

---

### Post by squaregoldfish on 2010-05-15
I've just achieved this.

At the top of /etc/init/gdm.conf, replace the lines:

```
start on (filesystem
          and started dbus
          and (graphics-device-added fb0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1
               or stopped udevtrigger))
```with the following:

```
start on runlevel []
```Steve.

---

