---
title: "Subdomains point to localhost"
date: 2011-03-31
forum: General Help
---

### Post by CloudedVision on 2011-03-31
I'm doing development on a site, let's call it mysite.com.  mysite.com and [www.mysite.com](www.mysite.com) works fine, but proxy.mysite.com and dev.mysite.com point to the LAMP stack running on my computer.  Pinging mysite.com gives me:

```
64 bytes from server.myhost.com (64.64.0.102): icmp_req=1 ttl=47 time=47.4 ms
```

Whereas dev.mysite.com gives me:

```
64 bytes from localhost.localdomain (127.0.0.1): icmp_req=1 ttl=64 time=0.031 ms
```

Subdomains of any other site work fine.  I am absolutely baffled.  What in the world could be causing this?  I haven't been messing around in /etc/hosts or anything like that.

---

### Post by falko on 2011-03-31
Is dev.mysite.com listed in /etc/hosts?

---

### Post by CloudedVision on 2011-03-31
No, not at all.

```
192.168.2.100   Cortana # Added by NetworkManager
127.0.0.1       localhost.localdomain   localhost
::1     Cortana localhost6.localdomain6 localhost6
127.0.1.1       Cortana

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

---

### Post by CloudedVision on 2011-03-31
Solved.  Cpanel made some funny DNS zone entries on my server.

---

