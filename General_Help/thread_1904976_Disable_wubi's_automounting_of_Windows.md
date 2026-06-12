---
title: "Disable wubi's automounting of Windows"
date: 2012-01-05
forum: General Help
---

### Post by Kinstonian on 2012-01-05
Is there a problem with stopping Wubi from auto-mounting the Windows partition and if not, what's the best way to stop it?

---

### Post by Anstice on 2012-01-05
Take a look at your filesystem table:

```
cat /etc/fstab
```

See if there is an entry that matches your windows partition in there using:

```
fdisk -l
```

If there is remove it or just comment it out to be on the safe side.

---

### Post by Kinstonian on 2012-01-05
I looked in the fstab and didn't see it... although it does show up in the mount command.  Unless I'm missing something wubi is doing something different.

---

### Post by bcbc on 2012-01-06
You can't unmount the /host partition because the virtual disk (root.disk) is on it.

---

### Post by Kinstonian on 2012-01-06
> **bcbc said:**
> You can't unmount the /host partition because the virtual disk (root.disk) is on it.

I was worried that might be a problem.  Oh well, thanks for the info.

---

