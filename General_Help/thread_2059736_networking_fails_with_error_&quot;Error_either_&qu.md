---
title: "networking fails with error &quot;Error: either &quot;dev&quot; is duplicate, or &quot;upp&quot; is a garbage"
date: 2012-09-18
forum: General Help
---

### Post by Jarretinha on 2012-09-18
Hi all,

I've a NIC with two interfaces. eth0 is statically set on a internal network and is working properly. eth1 will be used for external access using DHCP. The /etc/network/interfaces was set as usual. After some troubles with IT guys and a lot of instability and tests, eth1 stopped to work as expected.

Even when explicitly removed with ```
ip link set eth1 down
``` and completely removed from interfaces file, /etc/init.d/netwoking still brings it up. I think something is duplicated. During ifup, ssh restarts twice and an ip link set eth1 up give me this error, even when the iface is down:

```
Error: either "dev" is duplicate, or "upp" is a garbage
```

This error ocurrs even when the iface isn't described in interfaces. Am I forgetting something behind? Is there other config files besides interfaces? 

By the way, network-manager and related aren't installed.

---

