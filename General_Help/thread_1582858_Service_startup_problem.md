---
title: "Service startup problem"
date: 2010-09-27
forum: General Help
---

### Post by Francesco Ricci on 2010-09-27
Hi,
i have a problem with a statup of some services.

The service apache2 although is in /etc/rc* don't run at statup

```
 * /etc/rc0.d/K20apache2 -> ../init.d/apache2
 * /etc/rc1.d/K20apache2 -> ../init.d/apache2
 * /etc/rc6.d/K20apache2 -> ../init.d/apache2
 * /etc/rc2.d/S20apache2 -> ../init.d/apache2
 * /etc/rc3.d/S20apache2 -> ../init.d/apache2
 * /etc/rc4.d/S20apache2 -> ../init.d/apache2
 * /etc/rc5.d/S20apache2 -> ../init.d/apache2

```

The service ssh instead, although isn't in /etc/rc* but it run at every startup and i don't want this.
```
update-rc.d: warning: ssh start runlevel arguments (none) do not match LSB Default-Start values (2 3 4 5)
 System start/stop links for /etc/init.d/ssh do not exist.

```

The service ssh run too from /etc/network/if-up.d/ then i have removed the execution flag at the script


Where is the mistake? How i can do?

---

