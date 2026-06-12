---
title: "Network lost after move"
date: 2006-06-21
forum: General Help
---

### Post by Frihet on 2006-06-21
HP L2000 laptop. 32 bit 6.06.

Network works fine everytime the machine is started. If I move the machine to another network and start up, I have no connectivity. If I reboot (second start), connectivity is restored.

Odd.

---

### Post by IYY on 2006-06-21
Every time the machine is started, the dhclient command is called to get an IP address from the router (or cable/DSL modem). When you move the machine, this IP address is no longer valid, of course.

So, to reconnect:

```
sudo dhclient
```

---

### Post by blackjack6.21.91 on 2006-06-22
Try getting the network manager applet.  You shouldn't have to use the terminal every time.  I think it's available in the repos.

---

