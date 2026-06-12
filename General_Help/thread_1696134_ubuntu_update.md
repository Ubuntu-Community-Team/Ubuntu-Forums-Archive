---
title: "ubuntu update"
date: 2011-02-26
forum: General Help
---

### Post by dcool76 on 2011-02-26
I was wondering I notice my server jumps from .13 to 1.13 and then when I look at CPU shows update using 1.0 cpu and it will stay like that for along time till I kill it and the load goes back to .13 . I was wondering if it is getting stuck or is there a fix thanks.

---

### Post by plucky on 2011-02-27
> **dcool76 said:**
> I was wondering I notice my server jumps from .13 to 1.13 and then when I look at CPU shows update using 1.0 cpu and it will stay like that for along time till I kill it and the load goes back to .13 . I was wondering if it is getting stuck or is there a fix thanks.

It is probably trying to tell you there are updates to install.Have you tried running ```
sudo apt-get upgrade
```

I have found that "Update Manager" seems to use a lot of CPU cycles when waiting to install upgrades.

Good Luck

---

