---
title: "No Screens Error After Kernel Compile"
date: 2006-03-08
forum: General Help
---

### Post by henry95 on 2006-03-08
I re-compiled the same kernel version that i had just to test the proccess, but when it boots up i get a no screens error.  I can log in but no GUI.  Any ideas?

---

### Post by henry95 on 2006-03-08
The error says:

```

Using config file: "/etc/X11/org.config"
NVIDIA: No matching Device section for instance (BusID PCI:2:4:0)  found
FATAL: Module nvidia not found/
Failed to load the NVIDIA kernel module!
***Aborting***
(EE) Screens Found, but none have a usable configuration.
Fatal Server Error:
no screens found

```

---

### Post by henry95 on 2006-03-08
Never mind!

sudo dpkg-reconfigure xserver-xorg

did the trick. :p

---

