---
title: "Bind/DNS Problem"
date: 2010-01-07
forum: General Help
---

### Post by josephmcnelis on 2010-01-07
Hey All,

Im trying to set up Bind9 on my hardy VPS, ive have a few websites which i want to host but i can't seem to get Bind to work. When i dig for my domain i don't get an answer just some info in the Authority section.

(The ip address and domain name are made up, but are consistent with the setup ive got regarding their locations in files and such)
My VPS IP Address : **91.91.91.91** 
Forwarder IP Address 1 : **80.80.80.80**
Forwarder IP Address 2 : **81.81.81.81**
This is my set up so far:

**resolv.conf**
```
search mydomain.co.uk
nameserver 80.80.80.80
nameserver 81.81.81.81
```**named.conf.local**
```
// Consider adding the 1918 zones here, if they are not used in your
// organization
//include "/etc/bind/zones.rfc1918";

zone "mydomain.co.uk" in {
    type master;
    file "/etc/bind/zones/mydomain.co.uk.db";
    };

zone "91.91.91.in-addr.arpa" in {
    type master;
    file "/etc/bind/zones/rev.91.91.91.in-addr.arpa";
};
```**named.conf.options**
```
options {
recursion yes;
    directory "/var/cache/bind";

    // If there is a firewall between you and nameservers you want
    // to talk to, you might need to uncomment the query-source
    // directive below.  Previous versions of BIND always asked
    // questions using port 53, but BIND 8.1 and later use an unprivileged
    // port by default.

    // query-source address * port 53;

    // If your ISP provided one or more IP addresses for stable 
    // nameservers, you probably want to use them as forwarders.  
    // Uncomment the following block, and insert the addresses replacing 
    // the all-0's placeholder.

     forwarders {
        80.80.80.80;
        81.81.81.81;
     };

    auth-nxdomain no;    # conform to RFC1035
    listen-on-v6 { any; };
};
```[B]

mydomain.co.uk.db[/B]
```
$TTL 86400

mydomain.co.uk. IN SOA ns1.livedns.co.uk. admin.mydomain.co.uk. (
2 ; serial
3H ; refresh
1H ; retry
1W ; expire
1D ; ttl
)

; name servers
@    IN      NS      ns1.livedns.co.uk.
@    IN    NS    ns2.livedns.co.uk.

; Replace the IP address with the right IP addresses.
@    IN    A    91.91.91.91
www    IN    A    91.91.91.91
ns1    IN    A    91.91.91.91
ns2    IN    A    91.91.91.91

```**rev.91.91.91****.in-addr.arpa**
```
$TTL 604800  ;  604800seconds

@    IN    SOA   ns1.livedns.co.uk. admin.mydomain.co.uk. (
                              1 ; serial number
                              604800         ; refresh
                              86400        ; update retry
                              2419200         ; expiry
                              604800 )         ; minimum
                              
    IN      NS      ns1.livedns.co.uk.
    IN      NS      ns2.livedns.co.uk.
91    IN      PTR     www.mydomain.co.uk. ; qualified name

```Any help would be greatly appreciated

---

