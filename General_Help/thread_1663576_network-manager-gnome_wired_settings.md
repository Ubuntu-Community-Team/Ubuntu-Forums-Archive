---
title: "network-manager-gnome wired settings"
date: 2011-01-09
forum: General Help
---

### Post by COKEDUDE on 2011-01-09
Where are the network-manager-gnome wired settings stored? I want to copy my network-manager wired settings from one computer to another.

---

### Post by COKEDUDE on 2011-01-14
The user settings will be stored here. 

```
/home/userdirectory/.gconf/system/networking/connections
```

[http://www.arachnoid.com/linux/NetworkManager/](http://www.arachnoid.com/linux/NetworkManager/)

The System settings will be stored here. 


```
/etc/NetworkManager
```
```
/etc/NetworkManager/system-connections
```

---

