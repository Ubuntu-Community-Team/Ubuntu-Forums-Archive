---
title: "Root keeps owning my firefox cache folder"
date: 2011-07-30
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-07-30
Every time i login root owns the Cache folder i want to be the owner cause that is the way it should be
from fstab
```
tmpfs /home/chad/.mozilla/firefox/main.default/Cache tmpfs size=150M,nr_inodes=10k,mode=777            0       0

```this is run at shutdown
```
#!/bin/sh
rsync -av --delete /home/chad/.mozilla/firefox/main.default/Cache/ /home/chad/.mozilla/firefox/main.default/Cache_hdd/
rm -rf /home/chad/.mozilla/firefox/main.default/Cache/*
rm -rf /tmp/*
exit
```this is run at login (not as root)
```
#!/bin/sh
if [ ! -f /home/chad/.mozilla/firefox/main.default/Cache/_CACHE_MAP_ ]; then
    rsync -av --delete /home/chad/.mozilla/firefox/main.default/Cache_hdd/ /home/chad/.mozilla/firefox/main.default/Cache/
fi
exit 0
```

---

### Post by pqwoerituytrueiwoq on 2011-07-31
bump

---

### Post by pqwoerituytrueiwoq on 2011-08-04
no suggestions?

---

