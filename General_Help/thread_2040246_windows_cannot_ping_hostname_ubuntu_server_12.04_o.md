---
title: "windows cannot ping hostname ubuntu server 12.04 on a different vlan"
date: 2012-08-10
forum: General Help
---

### Post by mercxi on 2012-08-10
At my company I have 3 vlans, now any windows pc can ping the hostname of the ubuntu server that is on the same vlan as the ubuntu server.  However if I am on a different vlan, I can ping via ip but not via hostname.  Anyone know what I should do?

---

### Post by zero2xiii on 2012-08-10
Hay,

Adding the host names and IP's to each of the DNS/DHCP/Firewall/Routing settings should do the trick. This all dependant on the setup.

Each vlan should have its own "gateway" or DNS or simmilar functioning service to identify the hosts by name. But since they are not linked/synced between individual vlans, they will obviously not be able to route the host name query to another vlan if they are not included in the routing tables.

Cherz

---

### Post by mercxi on 2012-08-13
networking wise they are all linked, I can ping other computers hostnames on different vlans

---

