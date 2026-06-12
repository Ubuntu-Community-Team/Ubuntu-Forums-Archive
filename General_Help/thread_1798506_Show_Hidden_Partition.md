---
title: "Show Hidden Partition"
date: 2011-07-06
forum: General Help
---

### Post by vncatalin on 2011-07-06
Well i just installed ubuntu 11.04 using wubi, and i can't see the partition where i installed it. Using GParted i found that its mounted on /host. May be this the cause ? I do have some useful files on this partition and i need to make it visible.

---

### Post by Morbius1 on 2011-07-06
Open a terminal and type:
```
nautilus /host
```

It will open the Nautilus file manager to that location. 

Now go to Bookmarks > Add bookmark and it will show up in the left panel.

---

### Post by vncatalin on 2011-07-06
thanks a lot :D works

---

### Post by Frogs Hair on 2011-07-06
System Monitor > File System displays the host and Wubi partition .

---

### Post by Mark Phelps on 2011-07-06
> **vncatalin said:**
> Well i just installed ubuntu 11.04 using wubi, and i can't see the partition where i installed it. 

For future reference, a Wubi install does NOT create a partition; instead, it installs inside an existing partition.  In fact, it creates a single large file that behaves like a partition to Ubuntu.

---

