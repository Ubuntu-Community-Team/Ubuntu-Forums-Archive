---
title: "Missing partial in /var/cache/apt/archives"
date: 2009-07-29
forum: General Help
---

### Post by DeMus on 2009-07-29
A few days ago I cleared the cache of my updates and I also erased the directory partial. Now it can't update anymore. When I push Reload in Synaptic I get the message "Archive directory /var/cache/apt/archives/partial is missing." Also when I use Update manager.
What to do now? How to get this directory again?

---

### Post by credobyte on 2009-07-29
```
sudo mkdir /var/cache/apt/archives/partial

```

---

### Post by DeMus on 2009-07-29
> **credobyte said:**
> ```
sudo mkdir /var/cache/apt/archives/partial

```

Thanks a lot, that works. So,an empty folder is enough already?

---

### Post by credobyte on 2009-07-29
> **DeMus said:**
> Thanks a lot, that works. So,an empty folder is enough already?

```
dainis@ubuntu:/var/cache/apt/archives/partial$ ls -a
.  ..
```

Yes, for me it's always empty ( I think it's being used as a temporary folder when downloading/installing packages ).

---

