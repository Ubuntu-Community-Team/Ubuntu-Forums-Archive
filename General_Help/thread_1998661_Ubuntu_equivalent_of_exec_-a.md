---
title: "Ubuntu equivalent of exec -a ?"
date: 2012-06-07
forum: General Help
---

### Post by jabalsad on 2012-06-07
Hi,

I'm trying to find the ubuntu equivalent of exec -a some_name on RHEL (which basically executes a process as if it was executes by some_name)

Any ideas?

---

### Post by Vaphell on 2012-06-07
i see exec on both 10.04 and 12.04
```
exec: usage: exec [-cl] [-a name] [command [arguments ...]] [redirection ...]
```

---

