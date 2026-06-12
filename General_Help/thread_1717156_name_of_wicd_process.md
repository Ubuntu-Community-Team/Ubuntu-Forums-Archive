---
title: "name of wicd process?"
date: 2011-03-29
forum: General Help
---

### Post by matt_symes on 2011-03-29
Hi

Can someone with wicd installed tell me what name the  process calls itself can i can find it using pgrep. I don't have it installed on my machine.

i.e. For network manager something similar would be

```
matthew@matthew-laptop:~$ ps aux | grep NetworkManager
root       977  0.0  0.1  19720  3404 ?        Ssl  11:30   0:02 NetworkManager
...
```

It's probably wicd but i cant make that assumption.

Kind regards

---

### Post by Jose Catre-Vandis on 2011-03-29
ps aux | grep wicd

returns

wicd
wicd-daemon.py
../wicd/daemon/monitor.py

htop shows onlt the last two running on my cli system

---

### Post by matt_symes on 2011-03-29
Hi

> **Jose Catre-Vandis said:**
> ps aux | grep wicd

returns

wicd
wicd-daemon.py
../wicd/daemon/monitor.py

htop shows onlt the last two running on my cli system

You, sir, are a gentleman and a scholar.

I thought it might be wicd but you know the saying ...

'Assumption is the mother of all ****ups' ;)

Kind regards

---

### Post by Jose Catre-Vandis on 2011-03-29
Pleasure. Please mark as solved.

---

