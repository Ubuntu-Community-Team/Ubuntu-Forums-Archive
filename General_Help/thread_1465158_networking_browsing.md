---
title: "networking browsing"
date: 2010-04-29
forum: General Help
---

### Post by mcclunyboy on 2010-04-29
Hi,

how do i browse a windows network from my linux machine using commands ?

---

### Post by mcclunyboy on 2010-04-29
i should point out, samba has been installed on the linux box.

---

### Post by gmargo on 2010-04-29
Check out the tools in the **smbclient** package.  Start with **smbtree(1)**.
```

$ dpkg -L smbclient | grep /usr/bin/ | cut -c 10- | sort
findsmb
rpcclient
smbcacls
smbclient
smbcquotas
smbget
smbspool
smbtar
smbtree

```

---

