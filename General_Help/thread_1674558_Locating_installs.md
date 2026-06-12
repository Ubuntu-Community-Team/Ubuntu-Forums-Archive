---
title: "Locating installs"
date: 2011-01-24
forum: General Help
---

### Post by Sleven7 on 2011-01-24
I installed mii-diag and ethtool with Synaptic.

Properties on the two files shows ethtool installed in Utlities
and mii-diag in Networking (universe)

I've been thru the main menu looking to see if they were not selected to show in the menu. I can not find them.

I read the man page on ethtools, and would rather have a gui :D

Can anyone tell me where the tools are?

---

### Post by gmargo on 2011-01-24
> 
rather have a gui
[B]
ethtool(8)[/B] and **mii-diag(8)** are command line tools.  No gui.  No menu entry.

> 
where the tools are? 
```

$ which ethtool mii-diag
/sbin/ethtool
/usr/sbin/mii-diag

```

---

### Post by Sleven7 on 2011-01-24
Thanks gmargo

---

