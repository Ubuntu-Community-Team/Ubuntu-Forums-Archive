---
title: "ipconfig equivalent?"
date: 2011-08-19
forum: General Help
---

### Post by carmenat250 on 2011-08-19
I know you can run ifconfig to get your IP address, but there is to much detail with this command.

Is there a command similar to ipconfig that would give me just my IP address, subnet and default gateway?

---

### Post by matt_symes on 2011-08-19
Hi

```
ifconfig
```

EDIT:

Hmmm. Think i misread your question. Scratch the above.

Kind regards

---

### Post by thefasterblueone on 2011-08-19
```
ifconfig | grep "inet addr" ; echo gateway; route -n
```

---

### Post by jfed on 2011-08-19
[http://www.whatsmyip.org/](http://www.whatsmyip.org/) for your external ip

```
ifconfig -a
```

for your local and gateway, i agree there is much detail included in that command, but must of the important stuff is near the top, its also sorted by eth0, wlan, etc.

---

