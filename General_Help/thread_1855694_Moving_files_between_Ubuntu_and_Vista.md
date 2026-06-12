---
title: "Moving files between Ubuntu and Vista"
date: 2011-10-06
forum: General Help
---

### Post by elixau on 2011-10-06
Hello,

Is it possible to move files between Ubuntu and Vista without the internet? I installed Ubuntu with Wubi. Thanks!

---

### Post by bcbc on 2011-10-06
Yes. Wubi can access the windows host under the /host directory. Alt+F2, /host 

Or you can mount partitions.

I don't recommend moving important data to Wubi's virtual disk if you don't need to - the /host is safer for that.

---

