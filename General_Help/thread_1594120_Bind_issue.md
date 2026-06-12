---
title: "Bind issue"
date: 2010-10-12
forum: General Help
---

### Post by linustorl on 2010-10-12
Hi folks,

I have a problem which i cant figure out till today since yesterday.

I have an ubuntu box 8.04 hardy heron installed with bind9.

Everything is works fine for the bind except the reverse DNS, i mean on the net, others DNS seem doesn't to know the reverse address on my IP which i have set in the reverse zone.

I have an ip address starting from 114.57.164.64 till 79 with subnet 240.

Here is my zone file for the reverse

```
$TTL    604800
$ORIGIN 164.57.114.in-addr.arpa.
@       IN      SOA     nshwg.hwg.co.id. root.hwg.co.id. (
                         2010101209     ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
164.57.114.in-addr.arpa.        IN              NS      nshwg.hwg.co.id.
164.57.114.in-addr.arpa.        IN              NS      nshwg1.hwg.co.id.


66      IN      PTR     mail.hwg.co.id.
67      IN      PTR     nshwg.hwg.co.id.
69      IN      PTR     nshwg1.hwg.co.id.
```

Here is my named.conf

```
// This is the primary configuration file for the BIND DNS server named.
//
// Please read /usr/share/doc/bind9/README.Debian.gz for information on the
// structure of BIND configuration files in Debian, *BEFORE* you customize
// this configuration file.
//
// If you are just adding zones, please do that in /etc/bind/named.conf.local

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

zone "hwg.co.id" {
        type master;
        file "/etc/bind/zones/db.hwg.co.id";
        allow-transfer {
                114.57.164.69;
        };
};

zone "164.57.114.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/164.57.114.in-addr.arpa";
        allow-query { any;};
        allow-transfer {
                114.57.164.69;
        };

};
//include "/etc/bind/named.conf.local";
```

Any ideas what is going wrong in my configuration?? DNS on the net seem doesnt update with my reverse zone.

Please point me out and thanks before.

---

