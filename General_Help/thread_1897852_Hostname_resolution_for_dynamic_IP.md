---
title: "Hostname resolution for dynamic IP"
date: 2011-12-20
forum: General Help
---

### Post by rdnublx on 2011-12-20
I am logging remotely via LAN into a Linux (Ubuntu) machine. The server's IP address is set dynamically by DHCP. Obviously, once in a while this IP address gets changed by the DHCP server. Is there any way to set up an automatic resolution of the server's host name into the dynamic IP address?

Thank you

---

### Post by Lars Noodén on 2011-12-20
The solution depends on the topology of your network.  Is the server in question connecting directly to the ISP's network?  Or is it connecting via router or switch which then connects to the ISP's network?

For the part that connects to the ISP, you can set up a [dynamic DNS](https://help.ubuntu.com/community/DynamicDNS) account and use that.

For the router or switch, most of them can be configured to assign the same IP address to a specific MAC address.

---

### Post by rdnublx on 2011-12-20
Sorry, I did not specify that. No, it's not a direct connection to the ISP. Unfortunately, the sysadmin may be out of my reach, to set up this type of association between IP and MAC.

Thank you

---

