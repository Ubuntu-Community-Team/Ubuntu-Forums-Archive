---
title: "/etc/hosts vs. /etc/networks"
date: 2010-02-07
forum: General Help
---

### Post by duane-tech on 2010-02-07
I'm confused about the difference between /etc/networks and /etc/hosts.
They both seem to be domain lookup for static hosts. What is the difference between them?

---

### Post by gmargo on 2010-02-07
Static hosts go in /etc/hosts.  See the man pages for hosts(5) and networks(5).  It is highly unlikely you will ever need to touch the /etc/networks file.

---

### Post by rnerwein on 2010-02-07
hi
it's not so  highly unlikely
see man ifup --->
The  ifup  and  ifdown  commands  may be used to configure (or, respec&#8208;
       tively, deconfigure) network interfaces based on interface  definitions
       in the file /etc/network/interfaces.

ciao

---

### Post by falconindy on 2010-02-07
> **rnerwein said:**
> hi
it's not so  highly unlikely
see man ifup --->
The  ifup  and  ifdown  commands  may be used to configure (or, respec&#8208;
       tively, deconfigure) network interfaces based on interface  definitions
       in the file /etc/network/interfaces.

ciao

Correct. Except this is /etc/network/* and not /etc/networks. Much like /etc/hosts, the networks file lets you alias network entities, except we're dealing with entire networks now, instead of singular hosts. For example, if you wanted to alias the network 1.2.3.0, you could do something like:
```
foo.bar    1.2.3.0    baz.bar
```
Where baz.bar becomes an alias to foo.bar, pointing to the network 1.2.3.0.

---

### Post by duane-tech on 2010-02-11
So if I understand correctly, names, aliases and IP addresses for individual hosts go in /etc/hosts, and the same thing, but for networks, go in /etc/networks. Also, in most cases, DNS is used instead of these files.

/etc/networks doesn't exist in my Redhat systems. Is it new, used only in some distros, or not used/ignored if missing. If Redhat uses a different method, where is it?

---

### Post by Iowan on 2010-02-11
> **duane-tech said:**
> /etc/networks doesn't exist in my Redhat systems.  It doesn't exist on Ubuntu systems, either.

> **falconindy said:**
> Correct. Except this is /etc/network/* and not /etc/networks.

---

