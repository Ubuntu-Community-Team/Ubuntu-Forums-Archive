---
title: "Complete removal of Windows 7"
date: 2011-09-19
forum: General Help
---

### Post by TmacD on 2011-09-19
Hello, I currently have a dual boot system with Windows 7 and Ubuntu 11.04. I've had issues with getting my wireless card working, but now that it is, I would like to remove Windows 7. Are there any special ways of doing this, or should I just remove the Windows 7 and System Reserved partition?

---

### Post by TeoBigusGeekus on 2011-09-19
Fire up gparted and expand your linux partitions. As simple as that...

---

### Post by TmacD on 2011-09-19
Thanks, just making sure. I had issues getting Windows to boot up after removing the Ubuntu partition; wouldn't want the same thing happening again.

---

### Post by seawolf167 on 2011-09-19
> **TmacD said:**
> Thanks, just making sure. I had issues getting Windows to boot up after removing the Ubuntu partition; wouldn't want the same thing happening again.

Your issues here were because of the Grub MBR being present. Fortunately, this won't be the case the other way around - after you remove the Windows partition if you run

```
sudo update-grub
```

It'll remove the no-longer existant Windows 7 loader pointer

---

