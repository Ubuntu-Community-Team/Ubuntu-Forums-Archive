---
title: "local DNS how to?"
date: 2012-04-20
forum: General Help
---

### Post by benjax911 on 2012-04-20
I am in arrears and in need of assistance. Thank you to anyone, in advance, for any help.
 
I have configured three servers for the non-profit company for whom I volunteer. The servers are as follows:
zimbra 192.168.0.205 x64 v10.04
alfresco 192.168.0.207 x64 v10.04
lamp (www) 192.168.0.209 i386 v10.04
 
- I have installed ssh, bind9 and samba on all three.
-The zimbra server is fickle and requires zimbra installation after the DNS fix in which I seek.
- the lamp and alfresco, I have installed webmin and intend to install webmin on zimbra once completed
- Finally, I have installed phpmyadmin on lamp, prior to webmin intall
 
Everything seems to be working great in regards to intranet accessibilty. My registered domain name, however, lacks some important configuration. I am new to Linux in this area; windows is easily fudged. I can navigate to lamp and alfresco with ease. After my, so-called, DNS configuration I can serve up a test page from a remote source e.g. my android phone disconnected from the wi-fi. The windows boxes navigate internally without fail, as I am using one for my ssh client. My FQDN, that is working externally, is not accessible internally. I feel certain that it is a reverse pointer issue, however, in following various tech articles from wiki's, I seem to simply complicate matters. So... can I get away with the /etc/hosts file doing it's thing, install NIS and learn that, or continue trying to get bind9 configured appropriately (which is my ultimate desire...to do it right).
 
I feel that I'm asking a lot and that I write in an ambiguous fashion so I feel rotten in even posting my plight. Help would be much appreciated. The following are my configuration files that I have changed. Each file is delineated by <!-- --> tags:
 
/etc/bind/named.conf.local <!--
 
//
// Do any local configuration here
//
// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";
zone "benicula.com" IN {
type master;
file "/etc/bind/externals/db.benicula.com";
};
zone "themenofnehemiah.org" IN {
type master;
file "/etc/bind/externals/db.themenofnehemiah.org";
};
zone "0.168.192.in-addr.arpa" {
type master;
file "/etc/bind/db.192";
};
-->
 
/etc/bind/named.conf.default-zones <!--
 
// prime the server with knowledge of the root servers
zone "." IN {
type hint;
file "/etc/bind/db.root";
};
// be authoritative for the localhost forward and reverse zones, and for
// broadcast zones as per RFC 1912
zone "localhost" IN {
type master;
file "/etc/bind/db.local";
allow-update { none; };
};
zone "127.in-addr.arpa" IN {
type master;
file "/etc/bind/db.127";
allow-update { none; };
};
zone "0.in-addr.arpa" IN {
type master;
file "/etc/bind/db.0";
allow-update { none; };
};
zone "255.in-addr.arpa" IN {
type master;
file "/etc/bind/db.255";
allow-update { none; };
};
-->
 
/etc/bind/externals/db.benicula.com <!--
 
; benicula.com
;
$TTL 1D
$ORIGIN benicula.com.
@ IN SOA . root. (
30
8H
4H
4W
1D )
;
NS lamp
MX 10 zimbra
@ IN A 192.168.0.209
www IN CNAME lamp
localhost IN A 127.0.0.1
alfresco IN A 192.168.0.207
lamp IN A 192.168.0.209
mail IN A 192.168.0.205
zimbra IN A 192.168.0.205
 
/etc/bind/db.192 <!--
 
$ttl 38400
$ORIGIN 0.168.192.in-addr.arpa.
@ IN SOA . root. (
1334855228
10800
3600
604800
38400 )
IN NS localhost.
205 IN PTR zimbra.
207 IN PTR alfresco.
209 IN PTR www.
 
-->
 
/etc/hosts <!--
 
127.0.0.1 localhost localhost
127.0.1.1 lamp lamp
# The following lines are desirable for IPv6 capable hosts
::1 localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
 
-->
 
/etc/resolv.conf <!--
 
nameserver 192.168.0.209
nameserver 192.168.0.1
search ns1.sitelutions.com yns1.yahoo.com sbcglobal.net
 
-->
 
/etc/hostname <!--
 
lamp
 
-->
 
I am soooo lost. This is my first real experience with using linux in a production environment so I'm battling a learning curve.
 
Thanks....if you read this far,
benjax911

---

### Post by newbie-user on 2012-04-20
Okay, let's back all the way up. You don't need bind9 on all three servers unless you're doing that for redundancy. You also don't need to add to /etc/hosts because your DNS server will take care of all that. You just have to make sure that your DHCP server passes the correct DNS information to the clients.

If you want your FQDN the same externally as internally, then you have to set up your PTRs with the FQDN. In /etc/bind/db.192, change ```
205 IN PTR zimbra.
207 IN PTR alfresco.
209 IN PTR www.
```
to
```
205 IN PTR zimbra.[yourdomain].com
207 IN PTR alfresco.[yourdomain].com
209 IN PTR www.[yourdomain].com
```

Other than that, I think you'll be okay with the other settings.

---

### Post by SeijiSensei on 2012-04-20
I'd run bind9 on at least one of the other servers and make it a slave to the one you have set up.  The zones on the slave look similar to the ones on the master replacing:

```

zone "example.com" {
     type master;
     file "/path/to/my/zones/example.com";
};

```

with 

```

zone "example.com" {
     type slave;
     file "/path/to/my/zones/example.com";
     masters { ip.addr.of.master; };
};

```

Replace "ip.addr.of.master" with the master's IP. 

Next, in named.conf.options on the master add the following directive right before the closing brace at the bottom of that file:

```
allow-transfer { ip.addr.of.slave; };
```

or replace "ip.addr.of.slave" with a subnet declaration like 192.168.0.0/24.  Pay close attention to the semi-colons; they're all required.

Now any changes you make on the master will be automatically synchronized with the slave.  Configure your DHCP server to give out both machines as the name servers.

If you make a change to the master, you must increment the serial number in the zone file.  Usually I use a numbering scheme like "2012042001" for these serial numbers; if I need to make multiple changes on a single day, I just increment the last two-digit number. 

Run "sudo killall -HUP named" on the master after the change to reload the zone files.  The slave will update automatically. (If you have a firewall, make sure you permit connections to TCP and UDP port 53 on the master, and UDP port 53 on the slave.  The TCP connection is used for domain transfers.  The UDP port handles queries.)

---

### Post by benjax911 on 2012-04-20
Thank you for the excellent advice.  I am pleased with the Ubuntu community and happy to have switched from SuSe to Ubuntu.:guitar: Y'all Rock!

---

