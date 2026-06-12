---
title: "BIND9 problem"
date: 2009-06-29
forum: General Help
---

### Post by xiaomahe on 2009-06-29
hai, i had installed bind9, and i had already configured the named.conf.local into this

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "mysecure.com" {
type master;
file "/etc/bind/db.mysecure.com";
};


then i checked the named.conf to see if there is anything wrong in the configuration file by using sudo named-checkconf /etc/bind/named.conf

and then i create the db.mysecure.com using sudo nano /etc/bind/db.mysecure.com

and this is the content inside db.mysecure.com
$TTL 86400
      @ IN SOA mysecure.com. root.mysecure.com. (
      20080108
      28800
      3600
      604800
      38400)

      IN NS mysecure.com.
      IN MX 10 mail.mysecure.com.
      IN A 10.0.0.2

      www IN A 10.0.0.2
      mail IN A 10.0.0.2

after that, i tried to check the file again for errors using named-checkzone with sudo named-checkzone mysecure.com /etc/bin/mysecure.com and it come out error like this:
/etc/bind/db.mysecure.com:2: no current owner name
/etc/bind/db.mysecure.com:9: no current owner name
/etc/bind/db.mysecure.com:10: no current owner name
/etc/bind/db.mysecure.com:11: no current owner name
/etc/bind/db.mysecure.com:13: no current owner name
/etc/bind/db.mysecure.com:14: no current owner name
zone mysecure.com/IN: loading from master file /etc/bind/db.mysecure.com failed: no owner


what is wrong with that?

---

