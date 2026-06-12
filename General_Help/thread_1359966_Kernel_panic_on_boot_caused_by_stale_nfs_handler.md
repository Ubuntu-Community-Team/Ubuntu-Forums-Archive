---
title: "Kernel panic on boot caused by stale nfs handler"
date: 2009-12-20
forum: General Help
---

### Post by simpleAndrew on 2009-12-20
Hi everyone.

I have Ubuntu 9.04 netbook remix installed on my Asus Eee PC 901. Also i have a simple PC with Ubuntu 9.10 installed. 

Netbook does not start Ubuntu correctly because of kernel panic on booting.
It says: 
```
run-init: /sbin/init: Stale NFS file handle
[    9.225276] Kernel panic - not syncing: Attmepted to kill init!
```
and than simply hang down...

Could anyone give me a solution for this problem???

Before this problem I tried to pass a file by wifi network from my PC to netbook. To do this I opened a net-directory on netbook connected to directory on my PC. After passing the file I did not shut down netbook correctly and I think that this net-directory was left somewhere at premount scripts... But this is only my novice guess...

---

