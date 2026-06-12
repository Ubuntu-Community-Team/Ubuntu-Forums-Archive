---
title: "How to delete WIndows Shadow Copies VSS"
date: 2011-02-19
forum: General Help
---

### Post by Andy06 on 2011-02-19
I deleted Windows from my Notebook and am only rockin Ubuntu on this machine. On the (previously) shared Data Partition, there are dozens of GBs occupied by the Volume Shadow Copy Service backups (which I used with Windows) but now how do I get rid of these?

In Windows you could either turn off VSS/Restore under System Protection or alternatively use the Disk Cleanup Utility. How do I do this with Ubuntu?

Thanks

---

### Post by TeoBigusGeekus on 2011-02-19
Delete them?

---

### Post by Andy06 on 2011-02-19
LOL yes but how?

Where are they located?

---

### Post by CharlesA on 2011-02-19
Those are located in the system volume information directory are they not?

---

### Post by TeoBigusGeekus on 2011-02-19
You can do a 
```
du -ha
```
to the partition and see all files and folders with their sizes.

---

### Post by Andy06 on 2011-02-20
> **CharlesA said:**
> Those are located in the system volume information directory are they not?

Sweet. Where can I find it? Like what's the path 

Thanks :)

---

### Post by CharlesA on 2011-02-20
> **Andy06 said:**
> Sweet. Where can I find it? Like what's the path 

Thanks :)
Mount the data partition and look for that folder there.

---

