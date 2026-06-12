---
title: "Would this be correct procedure for reinstating default software sources list?"
date: 2011-03-11
forum: General Help
---

### Post by Rytron on 2011-03-11
Hi.

Would this be the correct procedure for reinstating the default software sources list?

Copy backed up default [COLOR="Indigo"]sources.list[/COLOR] back to [COLOR="Indigo"]/etc/apt/[/COLOR] and run:

```
sudo apt-get clean; cd /var/lib/apt; sudo mv lists lists.old; sudo mkdir -p lists/partial; sudo apt-get clean; sudo apt-get update
```

---

