---
title: "KARMIC - does &quot;bootlogd&quot; work?"
date: 2009-10-29
forum: General Help
---

### Post by emarkay on 2009-10-29
[FONT=monospace]"/etc/default/bootlogd"
gives this option:

"Run bootlogd at startup ?
BOOTLOGD_ENABLE=No"

Changing to "yes" still gives:

(Nothing has been logged yet.)

Anyone confirm?

FWIW, I have a swap issue boot message I need to transcribe - is there another way? 
[/FONT]

---

### Post by cariboo on 2009-10-29
Have you started the bootlog daemon? To enable it, type:

```
sudo update-rc.d bootlogd defaults
```

---

### Post by emarkay on 2009-10-29
> **cariboo907 said:**
> Have you started the bootlog daemon? To enable it, type:
```
sudo update-rc.d bootlogd defaults
```

Uh-oh???

```
sudo update-rc.d bootlogd defaults
update-rc.d: warning: bootlogd start runlevel arguments (2 3 4 5) do not match LSB Default-Start values (S)
update-rc.d: warning: bootlogd stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (none)
 Adding system startup for /etc/init.d/bootlogd ...
   /etc/rc0.d/K20bootlogd -> ../init.d/bootlogd
   /etc/rc1.d/K20bootlogd -> ../init.d/bootlogd
   /etc/rc6.d/K20bootlogd -> ../init.d/bootlogd
   /etc/rc2.d/S20bootlogd -> ../init.d/bootlogd
   /etc/rc3.d/S20bootlogd -> ../init.d/bootlogd
   /etc/rc4.d/S20bootlogd -> ../init.d/bootlogd
   /etc/rc5.d/S20bootlogd -> ../init.d/bootlogd

```

---

