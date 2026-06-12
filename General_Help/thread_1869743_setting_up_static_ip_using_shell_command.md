---
title: "setting up static ip using shell command"
date: 2011-10-26
forum: General Help
---

### Post by avee137 on 2011-10-26
Hi,

Is there a command in linux to set-up static ip from command prompt?
I don't want to change it through configuration files and any similar mechanism. I need to change it directly from command prompt.


Thanks in advance.

---

### Post by WorMzy on 2011-10-26
You can set a static IP using ifconfig and dhcpcd, e.g.

```
ifconfig eth1 192.168.0.20 && dhcpcd eth1 -s 192.168.0.20
```

---

### Post by avee137 on 2011-10-26
is there a way to set default gateway using command?

---

### Post by Vaphell on 2011-10-26
[http://linux-ip.net/html/basic-changing.html](http://linux-ip.net/html/basic-changing.html)

---

### Post by haqking on 2011-10-26
> **avee137 said:**
> is there a way to set default gateway using command?

```
route add default gw Address Interface
```

---

