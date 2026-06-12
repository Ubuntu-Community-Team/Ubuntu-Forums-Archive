---
title: "Stop Gnome from starting at boot"
date: 2010-09-25
forum: General Help
---

### Post by averlon on 2010-09-25
Hi,
how do I deactivate (not deinstall) GNOME from loading when I start my server?

---

### Post by cariboo on 2010-09-25
This question has nothing to do with Maverick, or gnome-shell, moved to General Help.

To stop the desktop from starting at boot-up, remove gdm:

```
sudo apt-get purge gdm
```

When you want to run a gui type:

```
startx
```

at the prompt.

---

### Post by 666f6f on 2010-09-25
or: ```
sudo mv /etc/init/gdm.conf /etc/init/gdm.conf.disabled
```

---

