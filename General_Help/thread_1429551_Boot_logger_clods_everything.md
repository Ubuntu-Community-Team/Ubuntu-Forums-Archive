---
title: "Boot logger clods everything"
date: 2010-03-14
forum: General Help
---

### Post by gjesvik on 2010-03-14
When I try to boot everything goes fine until:

"Starting boot logger bootlogd"

And there it stands

---

### Post by Barriehie on 2010-03-15
> **gjesvik said:**
> When I try to boot everything goes fine until:

"Starting boot logger bootlogd"

And there it stands

You can turn it off by editing /etc/default/bootlogd:
```

BOOTLOGD_ENABLE=No
```If you must see what's going on at boot time you can use **dmesg**.

HTH

---

