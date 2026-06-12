---
title: "Ubuntu 10 - howto install Virtual NIC?"
date: 2011-07-04
forum: General Help
---

### Post by Maciej Miklas on 2011-07-04
Hi,

Default installation uses "Network Connections" application - interfaces file is empty.... so I do not know how to add virtual IP address.....

Is there possibility to add virtual IP without deinstalling network-manager? 

I could follow this tutorial, but what about WLAN, will it work?
[http://www.liberiangeek.net/2010/04/how-to-quickly-create-multiple-virtual-network-interfaces-in-ubuntu/](http://www.liberiangeek.net/2010/04/how-to-quickly-create-multiple-virtual-network-interfaces-in-ubuntu/)

I would like to store such configuration: ** ifconfig eth0:1  inet  192.168.1.136  netmask  255.255.255.0 **


Thanks,
Maciej

---

### Post by dcstar on 2011-07-04
> **Maciej Miklas said:**
> Hi,

Default installation uses "Network Connections" application - interfaces file is empty.... so I do not know how to add virtual IP address.....

Is there possibility to add virtual IP without deinstalling network-manager? 

I could follow this tutorial, but what about WLAN, will it work?
[http://www.liberiangeek.net/2010/04/how-to-quickly-create-multiple-virtual-network-interfaces-in-ubuntu/](http://www.liberiangeek.net/2010/04/how-to-quickly-create-multiple-virtual-network-interfaces-in-ubuntu/)

I would like to store such configuration: ** ifconfig eth0:1  inet  192.168.1.136  netmask  255.255.255.0 **


Thanks,
Maciej

What is wrong with using the Network Manager?, you can add as many IP addresses to an interface as you like.

---

### Post by Maciej Miklas on 2011-07-04
how can I add [B]eth0:1 ? 
[/B]

---

