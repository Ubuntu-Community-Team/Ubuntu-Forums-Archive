---
title: "Connect to smb-folder via terminal"
date: 2009-10-03
forum: General Help
---

### Post by Raff1 on 2009-10-03
Hello! I opened nautilus and wrote ithe following n the address bar:
```
smb://path.to.network.place/username
```I got full access to my network place in nautilus, but however, I want to access this folder also via the terminal.  I just can't figure out where on my computer this folder appears to be mounted! First of all i just want to access it from ```
cd /path/to/folder
```Thanks in advance!

-Raff1

---

### Post by Raff1 on 2009-10-03
Is it possible to mount the network place directly to a known location where I can find it?

---

### Post by dcstar on 2009-10-03
> **Raff1 said:**
> Is it possible to mount the network place directly to a known location where I can find it?

AFAIK you can add entries to your /etc/fstab file to do this.

---

