---
title: "DHCPd problems"
date: 2006-05-17
forum: General Help
---

### Post by FitzChivalry on 2006-05-17
I've been having some big problems with dhcp3-server on Ubuntu Breezy...

Initially when I installed ubuntu on my server with dhcp3-server, it worked fine with the server IP as 157.215.43.79, subnet of 255.255.255.0 and a range from 157.215.43.85 to 157.215.43.250

Since I reinstalled ubuntu the dhcp3-server *refuses* to work, I've tried changing the subnet and even the IP, as well as changing dhcpd.conf around many a time and yet it still doesn't work.

Currently the IP is 10.10.0.2 with a subnet of 255.255.255.0... though I'd prefer the original 157.215.43.x network.

Current dhcpd.conf:
```

subnet 10.10.0.0 netmask 255.255.255.0 {
  range 10.10.0.10 10.10.0.50;
  option domain-name-servers 10.10.0.2;
  option routers 10.10.0.1;
}

```

The dhcp3-server won't even start, /var/log/daemon.log says "No subnet declaration for eth0 (10.10.0.2)"

Anyone have any ideas?

---

### Post by joft on 2006-05-17
Hi,

are you sure that your server's NIC also has a subnet of 255.255.255.0 ? (Remember, that in the old days the 10.x.x.x belonged to the group of "Class A " networks and though the default subnet of your server's NIC might be 255.0.0.0 .)

BTW: Don't know if I understand you right, but if your network is a private one, you shouldn't use 157.* . These are official IP's, for private networks you have to use 10.* or 192.168.* for example (see RFC 1918 ).

---

### Post by kh4nh on 2006-05-17
"option domain-name-servers 10.10.0.2"

wouldn't this be addresses of your DNS servers

---

