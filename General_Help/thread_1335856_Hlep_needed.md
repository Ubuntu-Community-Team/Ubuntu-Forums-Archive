---
title: "Hlep needed"
date: 2009-11-23
forum: General Help
---

### Post by truefriend on 2009-11-23
Hi
 
I only want to know if there is any option can i remove remote desktop viewer from the tab application/internet in a ristrictd user cause in my network there are few people who distrub others by using this.

---

### Post by prshah on 2009-11-23
> **truefriend said:**
> 
I only want to know if there is any option can i remove remote desktop viewer from the tab application/internet 

You can remove this using the menu editor; right click the menu, and choose "Edit menus" or press Alt_F2 and give the command```
alacarte
```

Note that users can _still_ run remote desktop by pressing Alt_F2 (or opening a terminal) and giving the command```
rdesktop
# OR
tsclient
``` so if you really, really want to block it you can remove it with the command```
sudo apt-get remove rdesktop
```

---

