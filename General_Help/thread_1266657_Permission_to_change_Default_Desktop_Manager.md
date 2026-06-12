---
title: "Permission to change Default Desktop Manager"
date: 2009-09-14
forum: General Help
---

### Post by avacomputers on 2009-09-14
I tried changing my default desktop manager using this code
```
sudo echo "/usr/sbin/gdm" >> /etc/X11/default-display-manager
```

And I get this error
```
bash: /etc/X11/default-display-manager: Permission denied

```

Please help.

---

### Post by Woody1987 on 2009-09-15
No need to do that. Log out and open the gdm menu and choose the other desktop you want. You will then be asked to make it default, select yes or no.

---

