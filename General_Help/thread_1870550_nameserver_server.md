---
title: "nameserver server"
date: 2011-10-27
forum: General Help
---

### Post by laviper on 2011-10-27
How to make the ns1.myserver.ru ns2.myserver.ru in ubuntu server 11.04?
Nic.lv is entry type:
myserver.com - A - 255.255.255.255
[www.myserver.com](www.myserver.com) - A - 255.255.255.255
mydomain.com requires only the recording NS type records. 
There is DNS Management, but it don't work. 
Maybe it's cos in mydomain.com I have a hosting, and I want to change it, cos I have my own server.:sad:

---

### Post by dcstar on 2011-10-28
> **laviper said:**
> How to make the ns1.myserver.ru ns2.myserver.ru in ubuntu server 11.04?
Nic.lv is entry type:
myserver.com - A - **255.255.255.255**
[www.myserver.com](www.myserver.com) - A - **255.255.255.255**
mydomain.com requires only the recording NS type records. 
There is DNS Management, but it don't work. 
Maybe it's cos in mydomain.com I have a hosting, and I want to change it, cos I have my own server.:sad:

Broadcast addresses are **not** valid IP addresses.

---

### Post by laviper on 2011-10-28
> **dcstar said:**
> Broadcast addresses are **not** valid IP addresses.
This is only example.

---

