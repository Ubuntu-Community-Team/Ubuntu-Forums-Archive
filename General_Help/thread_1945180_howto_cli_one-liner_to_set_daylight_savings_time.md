---
title: "howto: cli one-liner to set daylight savings time"
date: 2012-03-22
forum: General Help
---

### Post by la11111 on 2012-03-22
```
sudo date -s "+`date --date='next hour'`" ; sudo hwclock -w
```

spring forward like a boss ;)

---

