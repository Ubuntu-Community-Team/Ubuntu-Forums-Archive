---
title: "BIND/Webmin Reverse DNS only works locally"
date: 2011-08-24
forum: General Help
---

### Post by SloS13 on 2011-08-24
I'm in way over my head here.  I help run a very small hosting company.  We recently moved from Windows 2000 DNS to BIND on Ubuntu, configuring with Webmin.

I'm more comfortable with Windows so I'm using NSLOOKUP to test the rDNS.  

A,CNAME,MX records are working fine outside the network, but PTR records are not.  The only reason I need a PTR record working is because AOL rejects email servers without one.  I really appreciate any expertise you can lend.  I've been struggling with this for over a week :(


Here are the results from NSLOOKUP
```
> server 67.33.14.19
Default Server:  [67.33.14.19]
Address:  67.33.14.19

> 67.33.14.7
Server:  [67.33.14.19]
Address:  67.33.14.19

Name:    femailex.futrtech.com
Address:  67.33.14.7

> server 8.8.8.8
Default Server:  google-public-dns-a.google.com
Address:  8.8.8.8

> 67.33.14.7
Server:  google-public-dns-a.google.com
Address:  8.8.8.8

*** google-public-dns-a.google.com can't find 67.33.14.7: Server failed
>
```

---

