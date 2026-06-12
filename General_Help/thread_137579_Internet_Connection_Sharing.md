---
title: "Internet Connection Sharing"
date: 2006-02-28
forum: General Help
---

### Post by Bachstelze on 2006-02-28
Hi :)

Can anyone help me out with this ? The wiki page is not clear at all... In fact, when installing dhcp3-server, it just won't start, I always get this :

```
 * Starting DHCP server...                                               [fail]

```

---

### Post by fabiand on 2006-02-28
Hey,

please provide the output of
```

tail /var/log/messages

```

After a dhcp-server start ...

- fabiand

---

### Post by Bachstelze on 2006-02-28
Thanks for the hint, here it goes :

```
Feb 28 16:06:59 localhost dhcpd: Internet Systems Consortium DHCP Server V3.0.2
Feb 28 16:06:59 localhost dhcpd: Copyright 2004 Internet Systems Consortium.
Feb 28 16:06:59 localhost dhcpd: All rights reserved.
Feb 28 16:06:59 localhost dhcpd: For info, please visit http://www.isc.org/sw/dhcp/
Feb 28 16:06:59 localhost dhcpd: Wrote 0 leases to leases file.
Feb 28 16:07:00 localhost dhcpd:
Feb 28 16:07:14 localhost gconfd (root-9505): GConf server is not in use, shutting down.
Feb 28 16:07:14 localhost gconfd (root-9505): Exiting
Feb 28 16:21:48 localhost kernel: [4298808.687000] eth0: link down
Feb 28 16:21:50 localhost kernel: [4298810.644000] eth0: link up, 100Mbps, full-duplex, lpa 0x41E1

```

---

### Post by Bachstelze on 2006-02-28
Oh, it was just silly me, I made some mistkes in my dhcpd.conf ^^"

---

