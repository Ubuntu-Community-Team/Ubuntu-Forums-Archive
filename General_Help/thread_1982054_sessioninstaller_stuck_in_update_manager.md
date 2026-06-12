---
title: "sessioninstaller stuck in update manager"
date: 2012-05-17
forum: General Help
---

### Post by Cardale on 2012-05-17
I just upgraded from 11.10 to 12.04 and session installer is stuck in the update manager.

---

### Post by Cardale on 2012-05-18
Simple fix thanks to celthunder on irc

```
sudo apt-get update; sudo apt-get install -f sessioninstaller
```

---

