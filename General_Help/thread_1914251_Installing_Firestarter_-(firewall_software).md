---
title: "Installing Firestarter -(firewall software)"
date: 2012-01-24
forum: General Help
---

### Post by Georgiou on 2012-01-24
I'm new to ubuntu, so be kind please.

basicaly i installed firestarter as per the ubuntu software center.However when i excute i get a message saying

"fail to load system log"

Could some instruct me on what to do?

---

### Post by haqking on 2012-01-24
> **Georgiou said:**
> I'm new to ubuntu, so be kind please.

basicaly i installed firestarter as per the ubuntu software center.However when i excute i get a message saying

"fail to load system log"

Could some instruct me on what to do?

remove it and use UFW or GUFW.

Firestarter is an out of date project and buggy.

IPTables/Netfilter is the firewall bulit into the Linux kernel, all firestarter is a interface for it, and so is UFW and GUFW being a graphical one.

see here for a guide [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)

a simple configuration would be

```
sudo ufw default deny incoming && sudo ufw default deny outgoing
```

```
sudo ufw enable
```

But remove firestarter first or there will be a conflict which causes issues

---

