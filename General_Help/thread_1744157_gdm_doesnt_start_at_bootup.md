---
title: "gdm doesnt start at bootup"
date: 2011-04-30
forum: General Help
---

### Post by uShafee on 2011-04-30
Here is what happend. I installed SLIM and rebooted. gdm failed to start so I went to the terminal and ran gdm manually from there. Then i logged in and removed slim package, reinstalled gdm and rebooted. Gdm still fails to start at boot up. When i try to manually start it, i get the following warnings:

Warning: unable to load file 'etc/gdm/custom.conf'
Warning: unable to find users: no seat-id found

help?

---

### Post by uShafee on 2011-04-30
Bump

---

### Post by uShafee on 2011-04-30
bump

---

### Post by lidex on 2011-04-30
Try this:
```
sudo apt-get install --reinstall gdm && sudo dpkg-reconfigure gdm
```

---

