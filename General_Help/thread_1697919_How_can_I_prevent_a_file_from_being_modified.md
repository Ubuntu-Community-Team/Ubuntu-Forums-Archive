---
title: "How can I prevent a file from being modified?"
date: 2011-03-01
forum: General Help
---

### Post by Riin on 2011-03-01
In /etc/default/rcS I have set FSCKFIX=yes. This solves a recurring 'no init found' problem that prevents my machine from booting.

Occasionally however, the setting reverts (by itself somehow) to FSCKFIX=no. Thus my machine cannot boot. 

Is there a way that I can prevent this file from being changed?

---

### Post by TeoBigusGeekus on 2011-03-01
```
sudo chmod -x /etc/default/rcS
```

---

