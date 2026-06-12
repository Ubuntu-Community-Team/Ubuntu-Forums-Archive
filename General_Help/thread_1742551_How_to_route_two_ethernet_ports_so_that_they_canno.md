---
title: "How to route two ethernet ports so that they cannot loopback locally (same PC)"
date: 2011-04-29
forum: General Help
---

### Post by K3v|n on 2011-04-29
Hi,

I have a NIC with 2 Ethernet ports and I would like to force them to go around the Ethernet Switch so that I can test the throughput/BW.
```

eth0 = 192.168.1.100
eth1 = 192.168.1.101
```
I tried:
```

route add -host 192.168.1.101 eth0
route add -host 192.168.1.100 eth1

iperf -B 192.168.1.100 -s
iperf -B 192.168.1.101 -c 192.168.1.100
```
Returned:
```

0.0-10.0 sec  13.5 GBytes  11.6 Gbits/sec
```
... didn't work since these are 1Gb Ethernet ports. It probably went through the loopback local.

Does anyone know how to set this up?

Thanks :D

---

