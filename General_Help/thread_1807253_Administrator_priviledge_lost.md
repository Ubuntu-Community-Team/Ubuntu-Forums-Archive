---
title: "Administrator priviledge lost"
date: 2011-07-18
forum: General Help
---

### Post by Gen Vert on 2011-07-18
For example, unable to download new software or remove software.
In Terminal I get:[INDENT]xxx@xx-desktop:~$ users-admin

(users-admin:2604): atk-bridge-WARNING **: AT_SPI_REGISTRY was not started at session startup.

(users-admin:2604): atk-bridge-WARNING **: IOR not set.

(users-admin:2604): atk-bridge-WARNING **: Could not locate registry
[/INDENT](Wonder if this is relevant. Computer would not work: no signal. Friend cured it by unplugging and replugging memory boards.)

---

### Post by cipherboy_loc on 2011-07-18
Can you use sudo? Also, it looks to me like a core GNOME service isn't being started. I believe it has to do with keyring management, but not sure which one off the top of my head. 


Cipherboy

---

### Post by Gen Vert on 2011-07-24
What action should I request to see if sudo is working?

---

