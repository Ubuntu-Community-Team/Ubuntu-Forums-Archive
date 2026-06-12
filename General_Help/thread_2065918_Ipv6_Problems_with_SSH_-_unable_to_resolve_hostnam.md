---
title: "Ipv6 Problems with SSH - unable to resolve hostname"
date: 2012-10-03
forum: General Help
---

### Post by sdpagent on 2012-10-03
Ok so when i try to run this command from my office:
```
ssh -6 fe80::be76:4eff:fe08:f0%eth1
```
I get the following error:
```
ssh: Could not resolve hostname fe80::be76:4eff:fe08:f0%eth1: Name or service not known
```
However if I run the command the rackspace cloud server itself, I can ssh into myself successfully.

Can anyone tell me what I need to do to start working with ipv6? Do I need to manually configure a ipv6 DNS? Atm I have set the ipv4 DNS manually to google's 8.8.8.8 but have nothing set for ipv6.

Stu

---

### Post by Lars Noodén on 2012-10-03
If your infrastructure does not support IPv6, then your main option would be to create a tunnel and use that instead.  [https://wiki.ubuntu.com/IPv6#Getting_Connected](https://wiki.ubuntu.com/IPv6#Getting_Connected)

---

### Post by lemming465 on 2012-10-03
What distribution and version of Linux has the failing ssh?  A similar commands works OK for me on Ubuntu 11.04, for example.

---

### Post by lemming465 on 2012-10-03
Note that fe80::/64 addresses are link-local (LAN) scope only; you can't use them to get past routers.

---

