---
title: "BIND9 Setup - Jaunty"
date: 2010-08-06
forum: General Help
---

### Post by jonniie on 2010-08-06
I've got a VPS running with a fresh install of Ubuntu Jaunty.  I installed BIND9 and I'm trying to get it up and running.  I seem to be able to get a reverse lookup no problem for the domain but getting a forward lookup fails every time.

Any pointers would be appareciated!  I've included appropriate conf files below...

named.conf.local :
```

//
// Do any local configuration here
//

// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "jonquinn.com" {
        type master;
        file "/etc/bind/zones/jonquinn.com.db";
};

zone "216.59.209.in-addr.arpa" {
        type master;
        file "/etc/bind/zones/rev.216.59.209.in-addr.arpa";
};


```
named.conf.options :
```

options {
        directory "/var/cache/bind";

        // If there is a firewall between you and nameservers you want
        // to talk to, you may need to fix the firewall to allow multiple
        // ports to talk.  See http://www.kb.cert.org/vuls/id/800113

        // If your ISP provided one or more IP addresses for stable
        // nameservers, you probably want to use them as forwarders.
        // Uncomment the following block, and insert the addresses replacing
        // the all-0's placeholder.

//forwarders {
//      208.67.222.222;
//};

        auth-nxdomain no;    # conform to RFC1035
        listen-on-v6 { any; };
};

```
jonquinn.com.db
```

$TTL 38400
jonquinn.com. IN SOA ns.jonquinn.com. root.jonquinn.com. (
        2010080601;
        28800;
        3600;
        604800;
        38400
);

jonquinn.com.   IN      NS      ns.jonquinn.com.

ns              IN      A       209.59.216.18
www             IN      A       75.127.98.105

```
 rev.216.59.209.in-addr.arpa :
```

$TTL 86400
@       IN      SOA     ns.jonquinn.com. root (
                2007062001
                28800
                604800
                604800
                86400
)
@       IN      NS      ns.

18      IN      PTR     ns.jonquinn.com.

```

---

### Post by jonniie on 2010-08-06
Just like that I fixed it.  Stupid syntax error!!!

---

