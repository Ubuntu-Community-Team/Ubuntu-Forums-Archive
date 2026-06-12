---
title: "selectively slow internet - Ipv6 disabled, no change"
date: 2010-09-16
forum: General Help
---

### Post by Mzwo on 2010-09-16
Hi all,


I've ran into a strange internet-related problem.

the setting: Am at my parents', all other machines (exclusively windows) in the house have no trouble connecting wired or wireless.

I manage to connect either way as well, BUT: most pages will load very, very slowly (google, for instance), will stop half way through (my outlook web access) or not load at all. So far, there has been one notable exception: a forum I regularly visit (not ubuntuforums) loads lightning quick. 

I've kept an eye on network traffic and it would appear that every second or so a 52 byte packet is allowed past, but no more (apart from when I go to said forum, then traffic is normal).

updates and installs don't work either - or rather, they are som slow they appear to be static.

I've tried disabling Ipv6, stopped MoBlock, disabled Ipv6 in firefox, fiddled with connection settings - no luck. Since it doesn't matter whether I'm connected wireless or wired, I doubt the wifi driver is to blame.  

pings are normal.  

any suggestions?

Thanks, Matt

running 10.04

---

### Post by Mzwo on 2010-09-16
PS: just tried changing my DNS-servers as described [here]("https://store.opendns.com/setup/operatingsystem/ubuntu") - no change. 

](*,)

---

### Post by dcstar on 2010-09-18
> **Mzwo said:**
> Hi all,


I've ran into a strange internet-related problem.

the setting: Am at my parents', all other machines (exclusively windows) in the house have no trouble connecting wired or wireless.

I manage to connect either way as well, BUT: most pages will load very, very slowly (google, for instance), will stop half way through (my outlook web access) or not load at all. So far, there has been one notable exception: a forum I regularly visit (not ubuntuforums) loads lightning quick. 

I've kept an eye on network traffic and it would appear that every second or so a 52 byte packet is allowed past, but no more (apart from when I go to said forum, then traffic is normal).

updates and installs don't work either - or rather, they are som slow they appear to be static.

I've tried disabling Ipv6, stopped MoBlock, disabled Ipv6 in firefox, fiddled with connection settings - no luck. Since it doesn't matter whether I'm connected wireless or wired, I doubt the wifi driver is to blame.  

pings are normal.  

any suggestions?

Thanks, Matt

running 10.04

Drop the MTU from the default in the Network Manager (try 1454).

---

