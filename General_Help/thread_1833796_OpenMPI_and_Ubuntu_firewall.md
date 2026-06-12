---
title: "OpenMPI and Ubuntu firewall"
date: 2011-08-26
forum: General Help
---

### Post by Beowolf64 on 2011-08-26
Natty firewall is blocking OpenMPI on my cluster. Parallel application simply hangs unless firewall on master node is disabled. Firewall on slave nodes doesn't have to be disabled. The same things happens when master node is moved to another server.

ssh port is open both ways and passwordless connection is enabled.  Apparently allowing port 22 isn't enough for OpenMPI or something else is wrong.

This is how firewall is configured:
```
$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
22                         ALLOW       Anywhere

22                         ALLOW OUT   Anywhere

```

---

