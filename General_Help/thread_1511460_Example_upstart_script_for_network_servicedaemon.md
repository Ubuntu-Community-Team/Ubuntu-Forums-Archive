---
title: "Example upstart script for network service/daemon?"
date: 2010-06-16
forum: General Help
---

### Post by sofakng on 2010-06-16
I'd like to create a couple of upstart scripts for some network service daemons (eg. usenet downloading service, torrent service, media management services, etc).

Basically they should start after the network service is started and the system is running (runlevel 2?) but I'm just wondering if anybody has an example script or more specific start/stop conditions that I can use.

Thanks!

---

### Post by Brandon Williams on 2010-06-18
I don't have an example script, but the basic idea is that /etc/init/networking.conf is responsible for starting networking on the system, and a network service/daemon shouldn't be started until networking startup is complete. This startup condition should accomplish that:
```
start on (started networking)
```
If you want it to only start in a specific set of runlevels, then:
```
start on (runlevel [2345] and started networking)
```

---

