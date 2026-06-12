---
title: "Run python script at login screen"
date: 2012-09-15
forum: General Help
---

### Post by virpara on 2012-09-15
I use a python script to set brightness to zero.
```
#!/usr/bin/python

import dbus
bus = dbus.SessionBus()
proxy = bus.get_object('org.gnome.SettingsDaemon',
                       '/org/gnome/SettingsDaemon/Power')
iface = dbus.Interface(proxy, dbus_interface='org.gnome.SettingsDaemon.Power.Screen')
iface.SetPercentage(0)
```

I've put it in Startup Applications. It works only when I login. There is full brightness at login screen.

Where should I put this so that it sets brightness to zero at login screen?

---

### Post by Epodx64 on 2012-09-15
You might be able to stick it in here
/etc/lightdm/lightdm.conf
I dunno though though I looked around for a place to put it and can't really find anything.

---

### Post by virpara on 2012-09-15
but it is configuration file(which stores cofig data usually). It is not the one which isn't executed when lightdm starts.

---

