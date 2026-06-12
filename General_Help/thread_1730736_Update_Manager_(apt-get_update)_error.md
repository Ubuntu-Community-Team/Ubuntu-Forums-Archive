---
title: "Update Manager (apt-get update) error"
date: 2011-04-16
forum: General Help
---

### Post by arepaking on 2011-04-16
Hi Folks,

When executing the following command, I get this error message:

```
sudo apt-get update

GLib-GIO:ERROR:/build/buildd/glib2.0-2.28.5/./gio/gdbusconnection.c:2279:initable_init: assertion failed: (connection->initialization_error == NULL)
```

Any ideas what could be causing this problem? I tried goggling the error but it leads nowhere.

Thanks!

---

### Post by arepaking on 2011-04-16
A simple ```
sudo apt-get clean
``` command solved the problem

---

