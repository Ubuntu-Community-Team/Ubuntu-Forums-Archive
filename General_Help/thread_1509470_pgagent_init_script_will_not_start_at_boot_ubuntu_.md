---
title: "pgagent init script will not start at boot ubuntu server"
date: 2010-06-14
forum: General Help
---

### Post by jmcalpi on 2010-06-14
Is there any reason that a pgagent start-stop daemon init.d script will start on Ubuntu desktop 9.04, but the exact same script will not start at boot on Ubuntu Server 9.04 (with gnome). It starts with sudo /etc/init.d/pgagent start, but I would rather it start with reboot.

---

### Post by jmcalpi on 2010-06-15
No replies. Hmmm. Let me ask a more general question. Why would an init.d script run on unbuntu 9.04 desktop at boot, but not on ubuntu server 9.04?

---

### Post by richcoosa19 on 2010-11-17
> **jmcalpi said:**
> No replies. Hmmm. Let me ask a more general question. Why would an init.d script run on unbuntu 9.04 desktop at boot, but not on ubuntu server 9.04?

sudo update-rc.d pgadmin start 2 maybe?

---

