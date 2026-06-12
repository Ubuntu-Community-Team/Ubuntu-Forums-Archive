---
title: "firehol - runtime command failed to execute error 2"
date: 2012-01-08
forum: General Help
---

### Post by revaso on 2012-01-08
Kubuntu 11.10

My /etc/firehol/firehol.conf as minimal as possible just to demonstrate the error.
```
interface eth0 interface1
    server custom if1_udp_46198 udp/46198 any accept

```/etc/init.d/firehol restart

That's what I get.
```
ERROR   : # 1.
WHAT    : A runtime command failed to execute (returned error 2).
SOURCE  : line INIT of /etc/firehol/firehol.conf
COMMAND : /sbin/iptables -t filter -N in_interface1_if1_udp_46198_s1 
OUTPUT  : 
```There was a bug in past. But it should be fixed long time ago already. [https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017](https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017)

Dunno why I still get it on 11.10.

How to fix it?

---

