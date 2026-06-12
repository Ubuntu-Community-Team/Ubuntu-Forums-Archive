---
title: "How to limit traffic rate for users on server"
date: 2009-09-21
forum: General Help
---

### Post by [core] on 2009-09-21
Hello Everyone!
There are the following configuration:
Computer with Ubuntu like server which is used for internet destribution. Also every user can start torrent client on server thorough NX Server-NX Client solution from NoMachine.
Problem: how to limit speed for each user on server? I could use shaper for every IP but what about users on server?

---

### Post by mozkill on 2009-09-21
There are a bunch of linux distros to do this kind of thing.  Smoothwall, Untangle, and IPCop are three that I can think of off the top of my head.  You need to buy a $300+ hardware appliance to run it on though... but it would work.  LogicSupply is one such online place to buy the hardware.  [http://www.logicsupply.com/categories/firewall_systems](http://www.logicsupply.com/categories/firewall_systems)

[http://www.untangle.com/images/screenshots/Networking/qos.png](http://www.untangle.com/images/screenshots/Networking/qos.png)
[http://www.untangle.com/images/screenshots/protocolcontrol_maingui.png](http://www.untangle.com/images/screenshots/protocolcontrol_maingui.png)

---

### Post by [core] on 2009-09-22
Are there software solution?

---

### Post by mozkill on 2009-09-22
Sorry, I believe its possible by reconfiguring your linux kernel with certain modules that enable that sort of thing and then using iptables (rather than merely "ufw" to manage the firewall).  Its complicated though and beyond my ability at the moment.

---

### Post by [core] on 2009-09-27
Possible solution:
- iptables: mark packets base on uid 
- iptables: similar mark packets base on network intrefaces
 - tc: filter packets using fw
- using IMQ patch to create virtual interfaces and quque on this.

Thank you.

---

