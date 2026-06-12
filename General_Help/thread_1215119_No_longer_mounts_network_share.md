---
title: "No longer mounts network share"
date: 2009-07-16
forum: General Help
---

### Post by bryceowen on 2009-07-16
I don't know if this would fall under networking or what, but until recently, ubuntu was auto-mounting the network share I use here at work, but suddenly, it no longer works and I'm forced to manually mount it with 
mount -a.

The entry in my fstab file is:
```

//192.168.xxx.xxx/wwwroot	/mnt/win	cifs	username=xxx,password=xxx	0	0

```

As I said, everything had been working fine until just a few days ago. Anyone have a possible problem I could look for?

---

