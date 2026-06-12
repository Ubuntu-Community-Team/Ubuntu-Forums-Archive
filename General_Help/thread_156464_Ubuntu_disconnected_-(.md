---
title: "Ubuntu disconnected :-("
date: 2006-04-07
forum: General Help
---

### Post by vagmi.mudumbai on 2006-04-07
Hi,

I have installed Ubuntu on my laptop and I currently cannot go online as my rj45 socket is toast. Although I can copy files from my other computers on the internet to the USB drive. I badly need Glade, gstreamer-mad and gvim on my laptop but i cannot get them now. Does anybody know how to get these installed on a laptop which does not have network connection.

I am aware of the /var/cache/apt folder. Can something be done with that?


Regards,
Vagmi

---

### Post by trent dillman on 2006-04-07
Download the .deb files from packages.ubuntu.com (as well as dependencies) and use 

```
dpkg -i program_to_install_here.deb
```

---

