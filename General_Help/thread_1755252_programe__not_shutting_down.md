---
title: "programe  not shutting down"
date: 2011-05-11
forum: General Help
---

### Post by cowboy7305 on 2011-05-11
have ubunto 11.04 and when i shut down some programs thy look like thy have ,but if i have not rebooted computer when i want to open them again it says error still running and i can do nothing until i reboot ,is there any way to shut then down with out rebooting ,only started with this ver of ubuntu

---

### Post by cowboy7305 on 2011-05-17
bump

---

### Post by __Sun__ on 2011-05-17
Try:
```
pkill application-name
```

E.g., Suppose you are running gedit and want to close it.
You'll write:
```
pkill gedit
```

Simple, eh?
On that behalf, look at
```
man kill
```

---

