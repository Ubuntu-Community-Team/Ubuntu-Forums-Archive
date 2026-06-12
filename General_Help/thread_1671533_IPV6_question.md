---
title: "IPV6 question"
date: 2011-01-20
forum: General Help
---

### Post by smooch101 on 2011-01-20
Hello,

I've got a /64 range on my vps and would like to add them all so i can use them
currently i'm adding them like:
ifconfig eth0 inet6 add ipv6ip/64

Is there a way to add all of them in the prefix at once??

---

### Post by lemming465 on 2011-01-20
More details about what "add them all" is for would help.  You can't possibly want to add 2^62 address individually, or have that many actual hosts on-link (2 bits are lost to unicast/multicast and local/global flags from the host part.)

E.g. if you want to configure lots of addresses on a single server instance, you probably want to route the /64.  If in addition you want to forward addresses from other hosts on the same subnet, then you probably need to run radvd in addition.

What are you actually trying to do?

---

