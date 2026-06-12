---
title: "Nautilus in superuser mode?"
date: 2012-01-24
forum: General Help
---

### Post by woodyg on 2012-01-24
I have not been using Nautilus for a while, so am a bit rusty... is there a way to open a folder within Nautilus as super user (without having to open a terminal and sudo nautilus)?

---

### Post by papibe on 2012-01-24
Alt+F2 to run a command, then write 'gksudo nautilus'. Your password will be ask on the GUI.

Does that help?
Regards.

---

### Post by dcstar on 2012-01-24
> **woodyg said:**
> I have not been using Nautilus for a while, so am a bit rusty... is there a way to open a folder within Nautilus as super user (without having to open a terminal and sudo nautilus)?

Either install the **nautilus-gksu** package or use this launcher:

```
gksudo "dbus-launch nautilus --no-desktop --browser"
```

---

### Post by woodyg on 2012-01-25
> **dcstar said:**
> Either install the **nautilus-gksu** package

Didn't work for me (on 11.10), not even after applying this "[work-around]("http://ubuntuforums.org/showthread.php?t=1861721")". 


> **dcstar said:**
> or use this launcher:

```
gksudo "dbus-launch nautilus --no-desktop --browser"
```

I have been away from Ubuntu for a while... have been using Xubuntu instead. Realised creating a launcher can not be done simply by right-clicking the desktop. Sometimes Ubuntu is a bit of a pain... I may just install Thunar instead. Is less hassle...

---

