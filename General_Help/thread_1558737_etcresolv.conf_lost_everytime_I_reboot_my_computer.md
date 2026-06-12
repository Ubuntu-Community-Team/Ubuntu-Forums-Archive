---
title: "/etc/resolv.conf lost everytime I reboot my computer"
date: 2010-08-22
forum: General Help
---

### Post by type8code0 on 2010-08-22
Hi,

It appears that /etc/resolv.conf back to default everytime I reboot my computer. 

I've added these 2 lines to resolve some DNS issue.

> nameserver 8.8.8.8
nameserver 8.8.4.4
[https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html)

My pc get an ip address from router (DHCP)

Your advise to make /etc/resolv.conf untouchable even after reboot would be highly appreciated.

Thanks

---

### Post by pbrane on 2010-08-22
*/etc/resolv.conf* is overwritten when you acquire a new address. If you right-click on the networkmanager applet you can edit connections and add the DNS servers there. At least until someone tells you how to make */etc/resolv.conf* persistent.

---

