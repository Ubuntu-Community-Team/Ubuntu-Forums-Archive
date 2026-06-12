---
title: "Set NIC speedy to 100mbps"
date: 2006-04-05
forum: General Help
---

### Post by lnunes on 2006-04-05
Hi all!

One question... I have a pcmcia ethernet card 10/100mbps, but it only runs at 10mbps....

How can I set this to 100mbps? :confused:

---

### Post by localzuk on 2006-04-05
Have you got a 100Mbps hub/switch?

---

### Post by dcstar on 2006-04-05
[QUOTE=lnunes]Hi all!

One question... I have a pcmcia ethernet card 10/100mbps, but it only runs at 10mbps....

How can I set this to 100mbps? :confused:[/QUOTE]
ethtool

---

### Post by lnunes on 2006-04-06
When I run "ethtool -a eth0" it returns:

*Cannot get device pause settings: Operation not supported*

Actually all ethtool options returns me "*Operation not supported*"

:confused: :confused: :confused: :confused: :confused: :confused: :confused:

---

### Post by Zer0d on 2006-04-06
[QUOTE=lnunes]When I run "ethtool -a eth0" it returns:

*Cannot get device pause settings: Operation not supported*

Actually all ethtool options returns me "*Operation not supported*"

:confused: :confused: :confused: :confused: :confused: :confused: :confused:[/QUOTE]

Try to do it like this: 

```
ethtool eth0
```

---

### Post by lnunes on 2006-04-07
well, seems like a hardware conflict, or something like that...

I solve it putting another pcmcia....:neutral:

---

