---
title: "Vm ware network adapter not recognised on ubuntu server VM"
date: 2010-02-17
forum: General Help
---

### Post by satty8610 on 2010-02-17
Hi,
I installed a ubuntu server edition on a VMware workstation.
The problem is , when I added a network adapter (so, total 2 adapters now), the second one was not being shown in ifconfig.
On trying ifconfig eth1, I found that the 2nd adapter didn't have an ip address.

So, I installed ubuntu desktop edition on another VM, and this time it showed both the network adapters on doing ifconfig, and both had ip addresses.

Why doesn't this work with ubuntu server?

---

### Post by satty8610 on 2010-02-17
hey....i just found out.All it required was to change the following file:
/etc/network/interfaces
[HTML]auto eth1
iface eth1 inet dhcp[/HTML]

and then bringing up the 2nd ethernet card:
```
sudo ifup eth1
```

---

