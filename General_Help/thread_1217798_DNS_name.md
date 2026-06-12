---
title: "DNS name"
date: 2009-07-20
forum: General Help
---

### Post by mthalis on 2009-07-20
I'm setting local DNS server and using this tutorial [http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093), so according to that they ask to give DNS server name how can i find it.below shows my host file 
[B]
hosts.conf[/B]
```

127.0.0.1	localhost
192.168.101.232	gateway.itess.lk	gateway
192.168.20.253 ites-desktop.lk  
# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

My DNS server machine have two IP'S
192.168.101.232 -go internet
192.168.20.254- local network ip

192.168.20.253 -- my web server ip

Can i use **gateway** as my DNS server name.
Please reply.

---

### Post by mthalis on 2009-07-21
yes, Can use **gateway** as DNS server name

---

