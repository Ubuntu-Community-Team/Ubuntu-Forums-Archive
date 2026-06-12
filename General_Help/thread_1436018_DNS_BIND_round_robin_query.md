---
title: "DNS BIND round robin query"
date: 2010-03-22
forum: General Help
---

### Post by nish on 2010-03-22
Hello all,

I have configured bind9 to have 2 IP addresses for the same domain name.

$ nslookup [www.ip.testing.com](www.ip.testing.com)
Server:		10.129.33.241
Address:	10.129.33.241#53

Name:	[www.ip.testing.com](www.ip.testing.com)
Address: 10.12.212.15
Name:	[www.ip.testing.com](www.ip.testing.com)
Address: 10.129.33.241

As you can see, [www.ip.testing.com](www.ip.testing.com) has 2 IP addresses assigned to it. My concern is, why DNS server returns both addresses when queried for [www.ip.testing.com](www.ip.testing.com). Shouldn't it return single IP and let client query to that IP only? why to make client take decision (may be based on, longest prefix match) which IP to connect to?

Besides, is there any way to configure BIND9 to return only single IP address?

Any pointers will be appreciated.

Thanks

---

### Post by rnldpj on 2011-03-05
Check out this link,

[http://jackal777.wordpress.com/2011/03/05/ubuntu-10-10-bind-round-robin-howto/](http://jackal777.wordpress.com/2011/03/05/ubuntu-10-10-bind-round-robin-howto/)

---

