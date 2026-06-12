---
title: "Synaptic installation is stuck at about 75% for 15min. Kill Synaptic?"
date: 2010-06-29
forum: General Help
---

### Post by finny388 on 2010-06-29
I am trying to install btnx daemon and it has been stuck at about 75% for at least 15min.

How do "undo" and start again?

thx

---

### Post by philinux on 2010-06-29
> **finny388 said:**
> I am trying to install btnx daemon and it has been stuck at about 75% for at least 15min.

How do "undo" and start again?

thx

Yes if it still frozen kill off synaptic then this from a terminal.

```
sudo dpkg --configure -a
```

---

