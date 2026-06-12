---
title: "OSPFv6 routing using quagga"
date: 2012-03-19
forum: General Help
---

### Post by rbcssn on 2012-03-19
Hi,
I'm trying to configure ospfv6 and ospf for eth0 and eth1 on a router using quagga. For ospf6 I type: **telnet localhost 2606 **to configure ospfv6 and then **config t** then **router ospf** then **interface eth0 **then **ipv6 ospf6 priority 100**. But ospf6 isn't working. It's the same for ospf using **telnet localhost 2604**. I'm following the instructions from [http://openmaniak.com/quagga_tutorial.php](http://openmaniak.com/quagga_tutorial.php). Although hosts in the networks belonging to eth0 and eth1 can't ping the other network's hosts, I type **vtysh -c "show ip route"** and there's routes marked O for ospf. Any idea where I'm going wrong and how to configure it?

---

