---
title: "fstab troubles"
date: 2006-03-24
forum: General Help
---

### Post by Luggy on 2006-03-24
I recently paritioned a drive from fat32 to ext3 and I'm having some problems with re-editing my fstab.

I want to have the drive mounted on boot and I want to read and write to it while not being root ( this seems to be the only way I can get around it). 

Here is my fstab

```
/dev/hdb1       /mnt/storage  	ext3    rw,auto,user,exec	 0       1
```

Thanks bunches guys!

---

### Post by taurus on 2006-03-24
You can also use "umask=0000" in the fourth field, replacing rw, user, & exec.

---

### Post by akshaysrinivasan on 2006-03-25
try  defaults,umask=000

---

