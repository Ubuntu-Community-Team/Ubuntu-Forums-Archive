---
title: "Need help on bind9 configuration"
date: 2011-06-04
forum: General Help
---

### Post by Maanden on 2011-06-04
Hi 
I'm running ubuntu 11.04 on vmware and i have some troubles in configuring DNS server when i try to do nslookup command i always have this error 
 
root@ubuntu:/etc/bind# nslookup hamza
Server: 192.168.20.3
Address: 192.168.20.3#53
** server can't find hamza: NXDOMAIN
 
 
I've disabled DHCP on vmware and i've set a static ip address on /etc/network/interfaces file  and here are my configuration files
 
**_named.conf.local file_**
zone "mendari.lan" {
type master;
file "/etc/bind/db.mendari.lan";
forwarders{};
};
zone "20.168.192.in-addr.arpa" {
type master;
file "/etc/bind/rev.20.168.192.in-addr.arpa";
forwarders{}; 
};
 
 
 
_**Forword lookup zone file**_
$TTL 3D
@ IN SOA hamza.mendari.lan. admin.mendari.lan. (
2011061001;
28800;
3600;
604800;
38400
);
mendari.lan. IN NS hamza.mendari.lan.
hamza IN A 192.168.20.3.
 
 
 
_**Reverse lookup zone file**_
@ IN SOA hamza.mendari.lan. admin.mendari.lan.
2011061001
28800;
604800;
604800;
86400
);
IN NS hamza.mendari.lan.
3 IN PTR hamza.mendari.lan.
1 IN PTR gw.mendari.lan.
 
 
 
**_resolv.conf file_**
nameserver 192.168.20.3
search mendari.lan.

Regards.

---

### Post by Maanden on 2011-06-04
any one ???

---

### Post by Maanden on 2011-06-05
??????????

---

### Post by SeijiSensei on 2011-06-05
Try removing the "forwarders{}" directives.  They're only appropriate if another server is being used to resolve the domain.

Do you see any errors in the logs when you start bind?

Do you get a different result if you use the fully-qualified name hamza.mendari.lan instead of just the hostname?

---

