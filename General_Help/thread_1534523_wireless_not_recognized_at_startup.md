---
title: "wireless not recognized at startup?"
date: 2010-07-19
forum: General Help
---

### Post by Janitor-Blue on 2010-07-19
When I start ubuntu from being turned off, my network manager does not show wireless as an option, only wired (disconnected.) When I open a terminal and type "sudo modprobe rt3090sta" my wireless card  becomes available and It works just fine. THe only problem is that I dont want to have to open a terminal to get my wireless to work every time i turn on my computer. Does anyone know how to remedy this?

---

### Post by cavalier911 on 2010-07-19
Add it to /etc/modules

---

### Post by Janitor-Blue on 2010-07-19
add what to where?

---

### Post by cavalier911 on 2010-07-19
```
sudo nano /etc/modules
```

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
**rt3090sta**



Add whats in bold
Ctrl+x,y,enter to save

---

