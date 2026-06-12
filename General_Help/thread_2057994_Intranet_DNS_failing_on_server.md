---
title: "Intranet DNS failing on server"
date: 2012-09-14
forum: General Help
---

### Post by Don Barnett on 2012-09-14
I have a backroom network ip 192.168.1. with Ubuntu server.  I set up DNS about a year ago but it has never been reliable.  I went through the documentation and checked all of the bind files but I can not get it to work properly.  I do not get any errors when starting but I can not see the URL when I ping from my PC. If I ping the URL on the server it works fine.

I would appreciate any suggestions as to what is wrong.

Thanks 
Don

Here are the config files:

****** named.conf ************

include "/etc/bind/named.conf.options";

// prime the server with knowledge of the root servers
zone "." {
	type hint;
	file "/etc/bind/db.root";
};

// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912

zone "localhost" {
	type master;
	file "/etc/bind/db.local";
};

zone "127.in-addr.arpa" {
	type master;
	file "/etc/bind/db.127";
};

zone "0.in-addr.arpa" {
	type master;
	file "/etc/bind/db.0";
};

zone "255.in-addr.arpa" {
	type master;
	file "/etc/bind/db.255";
};

include "/etc/bind/named.conf.local";

****** named.conf.local ************

zone "farmtest.local" {
	type master;
	file "/etc/bind/db.farmtest.local";
};

zone "1.168.192.in-addr.arpa" {
	type master;
	notify no;
	file "/etc/bind/db.192";
};

****** named.conf.options ************

options {
	directory "/var/cache/bind";
forwarders {
	68.87.85.98;
	205.171.2.65;
};

	auth-nxdomain no;    # conform to RFC1035
	listen-on-v6 { any; };
};

****** db.farmtest.local ************

$TTL	604800
@	IN	SOA	ns.farmtest.local. root.farmtest.local. (
			    105		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	ns.farmtest.local.
ns	IN	A	192.168.1.155
box	IN	A	192.168.1.155

****** db.192 ************
$TTL	604800
@	IN	SOA	ns.farmtest.local. root.farmtest.local. (
			     99		; Serial
			 604800		; Refresh
			  86400		; Retry
			2419200		; Expire
			 604800 )	; Negative Cache TTL
;
@	IN	NS	ns.farmtest.local.
155	IN	PTR	ns.farmtest.local.

---

