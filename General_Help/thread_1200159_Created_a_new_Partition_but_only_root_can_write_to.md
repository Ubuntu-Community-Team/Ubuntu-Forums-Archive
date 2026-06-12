---
title: "Created a new Partition but only root can write to it?"
date: 2009-06-29
forum: General Help
---

### Post by FreakTimmah on 2009-06-29
I created an EX2 partition but for some reason only root has access so I can not move files to it with my account. Is there an easy way to give myself access? I'm running 9.04

---

### Post by credobyte on 2009-06-29
All newly created partitions are owned by root.

```
sudo chown +R user:user /partition_name
```
Replace /partition_name with where you've created it.
Replace user:user with your username ( eg. credobyte:credobyte ).

---

### Post by FreakTimmah on 2009-06-29
Thanks that worked! I appreciate the help:guitar:

---

