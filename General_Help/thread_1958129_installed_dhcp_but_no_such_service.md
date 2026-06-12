---
title: "installed dhcp but no such service"
date: 2012-04-13
forum: General Help
---

### Post by loolooyyyy on 2012-04-13
i have installed dhcp3-sever but there was nothing like dhcp.conf on my machine (apt-get install dhcp3-server)
then i installed dchp3-* , again nothing
service dhcp, service dhcp3, dhcpd, dhcp3-server....... nothing at all!
no dhcp.conf at /etc/dhcp3/ , the folder is totally empty
what am i doing wrong?!!

---

### Post by matt_symes on 2012-04-13
Hi

> **loolooyyyy said:**
> i have installed dhcp3-sever but there was nothing like dhcp.conf on my machine (apt-get install dhcp3-server)
then i installed dchp3-* , again nothing
service dhcp, service dhcp3, dhcpd, dhcp3-server....... nothing at all!
no dhcp.conf at /etc/dhcp3/ , the folder is totally empty
what am i doing wrong?!!

Have a look at

 ```
sudo /etc/init.d/isc-dhcp-server start
```

and 

```
/etc/defaults/isc-dhcp-server
```

Kind regards

---

### Post by loolooyyyy on 2012-04-14
thank you very much!

---

