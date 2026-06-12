---
title: "kde to gde"
date: 2009-12-07
forum: General Help
---

### Post by prabhanjan2906 on 2009-12-07
I installed kde on my ubuntu 9.04. How do i set gde as the default display manager?

---

### Post by BenAshton24 on 2009-12-07
Click on the session dropdown and select GNOME before you log in.

Ben.

---

### Post by prabhanjan2906 on 2009-12-07
kde has been set to default. i want to set it back to gnome. the display manager is kdm. i want to set it back to gdm. how can i do that?

---

### Post by lovinglinux on 2009-12-07
I'm not sure, but if you install gdm again, it will probably ask which one you want to use during the installation process.

```
sudo apt-get install gdm
```

---

### Post by sprince09 on 2009-12-07
This should work:

```
sudo dpkg-reconfigure gdm
```


Should bring up a menu at some point to let you pick KDE or GDM (or whatever else you might have installed) as your default DE.

---

