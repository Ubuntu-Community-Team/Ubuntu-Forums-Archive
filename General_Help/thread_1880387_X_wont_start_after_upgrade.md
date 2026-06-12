---
title: "X wont start after upgrade"
date: 2011-11-13
forum: General Help
---

### Post by renegadeandy on 2011-11-13
Hey guys.

I just did a distro upgrade from 10.04 to 11.04 ,whilst doing the upgrade i also enabled the ATI proprietary driver, when going to reboot when the upgrader said a restart is required X seg faults

from the log this is what is says :

```

loads fglrx
falls back to old probe: method foor fglrx
pcs database file <llalaa> not found
creating database
chipset found
amd video driver is running on a device belong to a group targeted for this release
loads 2 drivers 0 fglrx_drv.so
libfglrxdrm.so

couple of /usr/bin lines

then 

caught signal 11, segmentation fault
server aborting

```

I appreciate this is not the full log, becasue it is on my laptop - and is really hard to read because all the text is buggered slightly because of some driver issue...

Any suggested next steps?

---

