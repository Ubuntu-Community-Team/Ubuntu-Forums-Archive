---
title: "Cannot disable service autostart"
date: 2010-10-16
forum: General Help
---

### Post by p12i on 2010-10-16
I've noticed that serval services starts at boot, even if I disabled them with update-rc.d or remove symlinks from /etc/rc?.d directories.

I have troubles with:
* sshd
* smbd
* nmbd
* avahi-daemon

 # find /etc/rc?.d /etc/init.d | grep -E  '(smbd|ssh|nmbd|avahi)'
/etc/init.d/ssh
/etc/init.d/avahi-daemon
/etc/init.d/nmbd
/etc/init.d/smbd

I'am using Xubuntu 10.04. Maybe someone else know how to solve this problem?

---

