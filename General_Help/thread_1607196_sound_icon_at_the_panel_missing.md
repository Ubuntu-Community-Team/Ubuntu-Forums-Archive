---
title: "sound icon at the panel missing"
date: 2010-10-27
forum: General Help
---

### Post by safari09 on 2010-10-27
im using ubuntu 10.10. some how, i just lost my sound icon at top of the panel. how can i put it back? i try go to System-->Preferences-->Sound, and there is a msg appear (waiting for sound system to respond). but unfortunately there is nothing happen.fyi, my laptop still have the sound and before the icon appear at the panel. is it related to synaptic package manager?

---

### Post by hhh on 2010-10-27
It's called Indicator Applet in 10.04 and later, so right-click your panel and choose Add to Panel>Indicator Applet.

---

### Post by Romala on 2010-10-27
This can help [https://help.ubuntu.com/community/AddingProgramToSessionStartup](https://help.ubuntu.com/community/AddingProgramToSessionStartup)

Excuse me, it is not right. It is click left button on a panel and check "Add to panel..."

---

### Post by safari09 on 2010-10-28
im just do it but only the mail icon appear. any other way that i can do? anyway thank for the reply.

---

### Post by hhh on 2010-10-28
You can reset your panels to their defaults. In a terminal run```
gconftool-2 --recursive-unset /apps/panel
```
and then restart the panels (again in a terminal)
```
pkill gnome-panel
```

---

### Post by safari09 on 2010-10-30
ok.thank you guyz...

---

