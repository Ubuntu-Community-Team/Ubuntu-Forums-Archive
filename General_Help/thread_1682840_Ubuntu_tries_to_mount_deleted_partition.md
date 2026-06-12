---
title: "Ubuntu tries to mount deleted partition"
date: 2011-02-06
forum: General Help
---

### Post by Nostigex on 2011-02-06
On startup my computer tries to mount a partition which I deleted (called Misc) and combined with the space of another. I get this message:

> The disk drive for /media/Misc is not ready yet or not supported. Continue to wait, or press S to skip mounting or M for manual recovery.

I also notice that the folder for the drive is still listed in nautilus. How do I get rid of it once and for all?

---

### Post by stlsaint on 2011-02-06
Edit the fstab folder to remove the partition line causing it to look for the misc folder.

```
gksudo gedit /etc/fstab
```

---

### Post by mcduck on 2011-02-06
..and also delete the mount point (/media/Misc).

(stlsaint's  suggestion will get stop the system trying to mount the now-nonexistent partition and get rid of the error message, while removing the mount point will make the drive disappear from Nautilus)

---

### Post by Nostigex on 2011-02-06
Thanks.

---

