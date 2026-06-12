---
title: "How do I go from a console login to graphical?"
date: 2006-04-08
forum: General Help
---

### Post by LordRaiden on 2006-04-08
I know that when presented with the KDM login, it is possible login to the console (ALT-N). But how do I go from console back into the KDM graphical login. I tried "sudo startkde" but it gave an error.

---

### Post by dreamsINdigital on 2006-04-08
startx?  Not sure for KDE, but I think that does it for GNOME.

---

### Post by aysiu on 2006-04-08
```
sudo /etc/init.d/kdm restart
```

---

### Post by taurus on 2006-04-08
Also, no need to put sudo in front if you want to run startkde.

---

