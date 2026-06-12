---
title: "Firestarter"
date: 2009-12-06
forum: General Help
---

### Post by DeMus on 2009-12-06
Hi,

I installed Firestarter some time ago. Now, with a new internet connection which includes a modem with firewall and a router with firewall, there is no need any more to keep Firestarter.
How to uninstall it in a way that there are no rules anymore? I mean, in my PC, everything should be open to the LAN. No restrictions whatsoever. 
The router is blocking all external traffic (and is doing a very good job I might add) and I trust all my computers on the internal network.

Could somebody please advise me how to do this?

---

### Post by sikander3786 on 2009-12-06
Just go to Synaptic and mark Firestarter for un installation. Have a look at this if you have any problems.

[http://ubuntuforums.org/showthread.php?t=157262](http://ubuntuforums.org/showthread.php?t=157262)

---

### Post by DeMus on 2009-12-06
> **sikander3786 said:**
> Just go to Synaptic and mark Firestarter for un installation. Have a look at this if you have any problems.

[http://ubuntuforums.org/showthread.php?t=157262](http://ubuntuforums.org/showthread.php?t=157262)

Thank you for your answer. I did uninstall it as mentioned in the thread you wrote. I was afraid some firewall rules would still exist, blocking local traffic but it seems to be okay.
Thanks again.

---

### Post by iponeverything on 2010-01-03
Usually with firestarter you have to give the --purge option to dpkg get rid of the old rules.

something along the lines of:
```
dpkg --purge firestarter

```

---

