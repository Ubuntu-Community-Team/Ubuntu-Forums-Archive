---
title: "Can't Update Files"
date: 2010-07-25
forum: General Help
---

### Post by dovael on 2010-07-25
When I try to update via manager I get the following error message:
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'n' is not known on line 2 in source list /etc/apt/sources.list.d/kevin-mehall-pithos-daily-lucid.list, E:The list of sources could not be read.'
The file reads:
deb [http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu](http://ppa.launchpad.net/kevin-mehall/pithos-daily/ubuntu) lucid main
n

I tried to delete this file but can not override root permission.

---

### Post by howefield on 2010-07-25
> **dovael said:**
> I tried to delete this file but can not override root permission.

Try opening the file with elevated rights, eg.

```
gksudo gedit /etc/apt/sources.list.d/kevin-mehall-pithos-daily-lucid.list
```

---

### Post by dovael on 2010-07-25
Thank you. Thank you. You helped me solve the problem!

---

### Post by howefield on 2010-07-25
> **dovael said:**
> Thank you. Thank you. You helped me solve the problem!

You're welcome. You're welcome ;-)

---

