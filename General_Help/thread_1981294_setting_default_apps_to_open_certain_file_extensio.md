---
title: "setting default apps to open certain file extensions with a script"
date: 2012-05-16
forum: General Help
---

### Post by linuxcss on 2012-05-16
in xubuntu I would like to use a script to setup certains apps
to be default on certain file extensions

what and where can those files be found in xubuntu 11.10?

---

### Post by cmont899 on 2012-05-16
User specific defaults can be set here:
```
~/.local/share/applications/mimeapps.list
```

system wide defaults are set here:
```
/usr/share/applications/defaults.list
```

---

### Post by linuxcss on 2012-05-16
thank you

---

