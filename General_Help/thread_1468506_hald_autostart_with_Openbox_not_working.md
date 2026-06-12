---
title: "hald autostart with Openbox not working"
date: 2010-05-01
forum: General Help
---

### Post by MooPi on 2010-05-01
I'm trying to get the hald daemon to run at startup. It only starts if I request a drive and give admin privileges. On restart of pcmanfm drives are mounted. My autostart.sh files reads:
```
hald --daemon=yes &
```

---

