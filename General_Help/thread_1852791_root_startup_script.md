---
title: "root startup script"
date: 2011-09-30
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-09-30
i was setting up my desktop to work as a router using this
[http://linuxgazette.net/140/brownss.html](http://linuxgazette.net/140/brownss.html)
and i need to run a few commands at startup
```
ifconfig eth0:1 10.0.0.1 netmask 255.255.0.0
iptables -t nat -A POSTROUTING -j MASQUERADE
iptables -P FORWARD ACCEPT
```

---

### Post by dave01945 on 2011-09-30
you can add them to 

```
/etc/rc.local
```

they will be run at startup as root

---

### Post by pqwoerituytrueiwoq on 2011-09-30
thanks, works like a charm :)

---

