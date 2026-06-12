---
title: "Seagate external hard disk not being recognized by ubuntu 12.04"
date: 2012-09-19
forum: General Help
---

### Post by sai krish on 2012-09-19
Ubuntu does not detect my external seagate hard disk or any other pen drive connected to the ports. The ports are working absolutely fine on windows and the HD is being detected on windows. I ran lsusb and this is what it shows before and after connecting my hardisk  (same)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by dcstar on 2012-09-20
> **sai krish said:**
> Ubuntu does not detect my external seagate hard disk or any other pen drive connected to the ports. The ports are working absolutely fine on windows and the HD is being detected on windows. I ran lsusb and this is what it shows before and after connecting my hardisk  (same)

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Do this when you plug it in and post the last page:

```
dmesg
```

---

