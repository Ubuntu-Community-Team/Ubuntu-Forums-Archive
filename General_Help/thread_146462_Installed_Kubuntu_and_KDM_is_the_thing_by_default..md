---
title: "Installed Kubuntu and KDM is the thing by default..I want GDM back"
date: 2006-03-18
forum: General Help
---

### Post by sands on 2006-03-18
I installed kubuntu. I opted for KDM during the installation..now i want GDM back..Help me

---

### Post by Xian on 2006-03-18
If you already have Gnome installed, then open a terminal:
$ sudo dpkg-reconfigure gdm

---

### Post by aysiu on 2006-03-18
You can also ```
sudo gedit /etc/X11/default-display-manager
``` and change ```
/usr/bin/kdm
``` to ```
/usr/sbin/gdm
```

---

### Post by sands on 2006-03-18
tat Worked
Thnx

---

