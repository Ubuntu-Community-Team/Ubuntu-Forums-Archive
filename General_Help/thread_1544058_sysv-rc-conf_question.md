---
title: "sysv-rc-conf question"
date: 2010-08-02
forum: General Help
---

### Post by Gatesgamer33 on 2010-08-02
This is probably a stupid question, but.....

In sysv-rc-conf, I notice that lxde is an option to add to the boot. Would it be possible to use sysv-rc-conf to preload lxde?

---

### Post by sisco311 on 2010-08-02
If you have multiple desktop managers installed, then 
```
sudo dpkg-reconfigure lxdm
```
should allow you choose the default one.

---

