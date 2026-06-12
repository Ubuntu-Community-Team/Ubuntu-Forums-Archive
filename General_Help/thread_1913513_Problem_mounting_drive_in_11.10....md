---
title: "Problem mounting drive in 11.10..."
date: 2012-01-22
forum: General Help
---

### Post by Nixarter on 2012-01-22
I have an external drive and it gets power, boots up and everything...  but it doesn't show up on my Desktop or in the list of folders/drives in the file browser.  I tried sudo fdisk -l and it just returns partitions on sda (my laptop internal hard drive).  Any ideas?

---

### Post by searchfgold6789 on 2012-01-22
Try 'lsusb' instead. Any luck?

---

### Post by Nixarter on 2012-01-22
```
ubuntu@ubuntu:/$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

:(

---

### Post by Nixarter on 2012-01-22
Now I'm really worried.  I unplugged it and felt the drive itself... it is really hot.  Hopefully it is just a short in the pcb, and I can swap it out.

---

