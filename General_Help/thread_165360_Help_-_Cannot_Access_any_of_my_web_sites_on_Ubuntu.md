---
title: "Help - Cannot Access any of my web sites on Ubuntu 5.10"
date: 2006-04-24
forum: General Help
---

### Post by bloodniece on 2006-04-24
I'm not sure what happened (hacker, me, other) 
I cannot reach any of the web sites hosted on my ubuntu server.
Neither localhost or mydomain.com works.  The only thing that does work is Webmin running on port 10000.  My NAT is setup to forward 80, 443, and 10000 to the Ubuntu box.
Stats:
Apache2
php5
mysql5
rails 1.12
static ip
5 virtual hosts running but inaccessible locally or remotely.
I have not changed permissions recently.

any help is appreciated.

---

### Post by bswilson on 2006-04-24
Perhaps you could share some more details?  Are you running a firewall?  If so, what is it (package and version, etc.)?  Are you using firestarter?  Have you looked at your /etc/hosts file for any strange modifications?

---

