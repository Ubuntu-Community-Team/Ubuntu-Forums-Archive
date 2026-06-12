---
title: "How to keep proceess running on EC2 (Ubuntu) while disconnecting?"
date: 2010-04-08
forum: General Help
---

### Post by omshiralkar on 2010-04-08
Hi All,
We have a new EC2 instance which has Ubuntu OS.
When I connect it through putty and start any process e.g. tomcat server, I can ping that server from my local machine and it works fine. But as soon as I disconnect through putty, that server goes down. :(
Even, I tried to run it as a background  process (using &) but did not work.
Any suggestions please??

---

### Post by dcstar on 2010-04-09
> **omshiralkar said:**
> Hi All,
We have a new EC2 instance which has Ubuntu OS.
When I connect it through putty and start any process e.g. tomcat server, I can ping that server from my local machine and it works fine. But as soon as I disconnect through putty, that server goes down. :(
Even, I tried to run it as a background  process (using &) but did not work.
Any suggestions please??

```
man nohup
```

---

