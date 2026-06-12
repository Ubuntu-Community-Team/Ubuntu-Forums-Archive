---
title: "iptables quota help"
date: 2009-09-01
forum: General Help
---

### Post by SpinningAround on 2009-09-01
Hello, I'm trying to configure --quota option in iptables so it count both inbound and outbound traffic as one then drop the connection, but I simply don't know how.

The following don't work sadly
```
:~$ iptables -m quota --quota 2147483648 -j ACCEPT
iptables v1.4.1.1: no command specified
Try `iptables -h' or 'iptables --help' for more information.
```

Something that I also thinking about is how to get iptables to drop the connection when the quota is at 0, this might be a problem since I got a few rules that allow outbound traffic (http,https,ftp).

---

