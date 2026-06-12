---
title: "HDD not detected"
date: 2012-03-31
forum: General Help
---

### Post by morgred on 2012-03-31
I have 2 HDDs, a 250 GB drive and a 320 GB drive both SATA. I have installed windows xp on the 250 one and from within windows i installed ubuntu on the same drive. All good but ubuntu doesn't see my other disk. How can i solve that?

---

### Post by morgred on 2012-03-31
I beg you pardon, it doesn't see the disk it is installed on, not the other.

---

### Post by morgred on 2012-04-01
come on, somebody?

---

### Post by -LynX- on 2012-04-01
Type this on terminal :

```
cat /etc/fstab
```

What's the output?

---

### Post by mcduck on 2012-04-01
> **morgred said:**
> I beg you pardon, it doesn't see the disk it is installed on, not the other.

If the system is booting and running, then it sure does see the disk it's installed on... ;)

What makes you think it's not working correctly?

Also, if you did a Wubi install the windows partition (within which Ubuntu would be installed) should be mounted at /host.

---

