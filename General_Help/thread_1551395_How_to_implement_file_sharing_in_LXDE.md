---
title: "How to implement file sharing in LXDE"
date: 2010-08-12
forum: General Help
---

### Post by rmcellig on 2010-08-12
I just installed LXDE on my PC to try it out. I can't figure out how to implement file sharing. I used the Synaptic Package manager to install LXDE.

---

### Post by Morbius1 on 2010-08-12
If your talking about samba file sharing:

To share folders to others on the network install:
```
system-config-samba
samba-common-bin
```To access shares on other machines in your network install:
```
gigolo
gvfs-fuse

```

---

