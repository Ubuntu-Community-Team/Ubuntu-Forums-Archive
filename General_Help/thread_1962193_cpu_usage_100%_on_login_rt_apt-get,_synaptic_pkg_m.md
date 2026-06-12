---
title: "cpu usage 100% on login r/t apt-get, synaptic pkg manager"
date: 2012-04-20
forum: General Help
---

### Post by txducker on 2012-04-20
A post on problems I had and what I did to fix them.

**Problem:** CPU usage at 100% on login. System monitor showed apt-get, synaptic package manager, and aptchk? using all the CPU. The system felt unusually slow. I tried killing the processes and the CPU usage went down. When I would try to open the software center or update the system, nothing would happen. When I ran the following code,  the update would hang/stay at 6% and CPU usage would go to 100%.
```
sudo apt-get update
```


**Solution:**
From command line, I ran then following code.
```
sudo rm /var/lib/dpkg/lock
sudo apt-get update
```

I hope this helps you if you have the same problem.

---

