---
title: "Determining RAID Array"
date: 2012-08-11
forum: General Help
---

### Post by Ubun2to on 2012-08-11
How do you determine what type of RAID array you have? (RAID 0, 1, etc.). I know the RAID array is working, as it shows up on the Disk Utility, and I know it's a PCI card controller.
I'm working with an old server that was literally just collecting dust for years.

---

### Post by Habitual on 2012-08-12
```
cat /proc/mdstat
```

---

### Post by Ubun2to on 2012-08-12
> **Habitual said:**
> ```
cat /proc/mdstat
```

Thanks. I figured it was a RAID 0 array.

---

