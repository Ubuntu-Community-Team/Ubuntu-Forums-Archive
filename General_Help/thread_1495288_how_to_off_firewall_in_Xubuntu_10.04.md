---
title: "how to off firewall in Xubuntu 10.04?"
date: 2010-05-27
forum: General Help
---

### Post by gads on 2010-05-27
Hi, how can I off the firewall in Xubuntu 10.04? im new with it, please help me...

---

### Post by darolu on 2010-05-27
In a Terminal:
```
sudo ufw disable
```

---

### Post by gads on 2010-05-27
thanks darolu ^_^

---

### Post by 3rdalbum on 2010-05-28
> **gads said:**
> Hi, how can I off the firewall in Xubuntu 10.04?

The opposite way to how you turned it on.

Xubuntu ships with the firewall disabled by default, so if you haven't turned it on, then you are probably firewalled at your modem/router. You can't turn the modem's firewall off, but you can forward ports to your computer.

---

