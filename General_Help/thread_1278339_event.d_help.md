---
title: "event.d help"
date: 2009-09-29
forum: General Help
---

### Post by Psycho.mario on 2009-09-29
I have a script (?) that is in /dev/event.d/ which puts getty on my rfcomm0 serial, however, /dev/rfcomm0 is only there when i connect it. I don't want this conection initialised on boot, but i still want to be able to use the script when rfcomm0 is created

How can i accomplish this?

The script:
```
# rfcomm0 - getty
#
# This service maintains a getty on rfcomm0 from the point the system is
# started until it is shut down again.

start on runlevel 2
start on runlevel 3
start on runlevel 4
start on runlevel 5
start on stopped rfcomm0

stop on shutdown

respawn
exec /sbin/getty 115200 rfcomm0
```

Thanks

---

### Post by Psycho.mario on 2009-09-29
//Bump

---

