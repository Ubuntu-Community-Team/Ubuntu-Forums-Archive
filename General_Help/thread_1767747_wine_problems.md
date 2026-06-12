---
title: "wine problems"
date: 2011-05-26
forum: General Help
---

### Post by DTKCloud on 2011-05-26
im trying to install steam on terminal and i keep getting this


wine client error:0: version mismatch 402/417.
Your wineserver binary was not upgraded correctly,
or you have an older one somewhere in your PATH.
Or maybe the wrong wineserver is still running?

---

### Post by seawolf167 on 2011-05-26
Welcome to the forums!

First thing I would do is check to ensure that Wine is up-to-date

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install wine
```

The instructions and tests as to what works with Steam in Wine and what doesn't can be found [here]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=19444").

---

