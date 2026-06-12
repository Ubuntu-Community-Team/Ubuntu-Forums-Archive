---
title: "Updates notifier"
date: 2010-09-13
forum: General Help
---

### Post by Clauu on 2010-09-13
Hi,
Just upgraded to 10.04 lts(fresh install) from 9.10 server but now when I'm login via ssh or directly there is no more checks for updates and no more notifier about what packages could be updated , something like this - ```
5 packages can be updated. 
5 updates are security updates.
```How to activate this option ?

---

### Post by Clauu on 2010-09-13
bump

---

### Post by Clauu on 2010-09-13
Found it .. it was enabled backports repository in sources - ```
# deb http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse

```

---

