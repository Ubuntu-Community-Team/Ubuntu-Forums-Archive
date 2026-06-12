---
title: "DHCP problem"
date: 2006-02-22
forum: General Help
---

### Post by pgavin on 2006-02-22
I'm having a problem with DHCP.  My ISP usually provides its customers an IP address that is behind a NAT, but for a fee you can get an Internet accessible IP.  The ISP allocates a 10.x.x.x IP to the MAC address of your computer, which you are supposed to get through DHCP.  This address has all traffic for some Internet IP address (68.x.x.x) routed to it.  If I boot into windows or into other Linux distros (I've tried Gentoo's LiveCD and DSL) the correct address (10.254.0.4) is retrieved through DHCP.  But Ubuntu always wants to pull a different address (10.254.10.1 or something like that), not the one my ISP has allocated me.  (The address that Ubuntu retrieves is behind the NAT). Does anyone know why this would happen?

Thanks

---

