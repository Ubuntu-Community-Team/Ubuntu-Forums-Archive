---
title: "Apache: preventing from listening for incoming connections"
date: 2009-10-20
forum: General Help
---

### Post by WestCity on 2009-10-20
Hi!

I will use Apache only as a development server. Is it secure by default, or I must prevent it from listening for incoming connections (by editing "ports.conf" file)?

If I must edit it, where to write my IP? This is code from "ports.conf" file:

```
# If you just change the port or add more ports here, you will likely also
# have to change the VirtualHost statement in
# /etc/apache2/sites-enabled/000-default
# This is also true if you have upgraded from before 2.2.9-3 (i.e. from
# Debian etch). See /usr/share/doc/apache2.2-common/NEWS.Debian.gz and
# README.Debian.gz

NameVirtualHost *:80
Listen 80

<IfModule mod_ssl.c>
    # SSL name based virtual hosts are not yet supported, therefore no
    # NameVirtualHost statement here
    Listen 443
</IfModule>
```

1) Here: NameVirtualHost *:80 -> NameVirtualHost my.IP.is.here:80

2) Here: Listen 80 -> Listen my.IP.is.here:80

3) Here: Listen 443 -> Listen my.IP.is.here:443

Or maybe only 2-3, or all 3 must be edited?

Thanks in advance! ;-)

---

### Post by Cuddles McKitten on 2009-10-20
Ubuntu, by default, sets up iptables rules that disallow any incoming connections.  You'll have to fix your iptables rules first (if you haven't already).

Assuming you don't already know how to use iptables and don't want to learn, you can use Firestarter (in the repos) to allow incoming connections pretty easily.

---

