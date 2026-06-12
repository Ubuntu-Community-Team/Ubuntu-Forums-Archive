---
title: "can't get permanant location entry nautilus"
date: 2012-03-18
forum: General Help
---

### Post by dez93_2000 on 2012-03-18
Hi. Using the gconf-editor trick to change "use location entry" to 'true' doesn't seem to work for me, i.e. when i open nautilus i still have breadcrumbs and have to use ctrl+L to change. Can anyone think why this might be?
Using configuration editor (gui) I've checked and the setting is still correct...

Thanks

Dez

---

### Post by mc4man on 2012-03-19
**IF** you're on 11.10 it's set in gsettings, so either run below command or install  dconf-tools, open dconf-editor & look in org.gnome.nautilus.preferences

 ```
gsettings set org.gnome.nautilus.preferences always-use-location-entry true
```

---

### Post by dez93_2000 on 2012-03-20
awesome, thank you sir.

---

