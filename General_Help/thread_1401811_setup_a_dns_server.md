---
title: "setup a dns server"
date: 2010-02-08
forum: General Help
---

### Post by harry_bk on 2010-02-08
Hi everybody, I am trying to configure a mail server on ubuntu based on  postfix following a tutorial of flurdy. But now the basic part of this  tutorial is working(I am able to send messages to virtual addresses and  domains). But I tried to setup a DNS server on ubuntu and I've got two problems:
-first, my /etc/resolv.conf is always changing and I have a file like this:
 domain: home
 search:home
 nameserver:192.168.1.1 which is the IP address of my router.
-My zone file is like this:
 $ttl 86400
@ IN SOA mta.reseau.loc. mail.reseau.loc. (
2008061801
21600
3600
604800
86400 )
;RECORD "A" DNS <-> CLASSICAL IP
@ IN NS mail.aritafric.com
IN MX 10 mail.aritafric
IN A 192.168.0.12
mail IN A 192.168.0.12
mta IN A 192.168.0.12
;ENREGISTREMENT MESSAGERIE
reseau.loc. IN MX 10 aritafric

my reverse dns is like this: 
@ IN SOA aritafric.com root.aritafric.com. (
2006081401;
28800;
604800;
604800;
86400);
IN NS aritafric.aritafric.com
12 IN PTR aritafric.aritafric.com

But when I excute the command dig aritafric.com, the MX part doesn't appear on the result as showed in a tutorial I read and I have a screen like this:

So what could be the solution??

P.S I'm running the ubuntu 9.10 on vmware using bridge. and we have a router with dhcp enabled

---

### Post by jigsaws on 2010-02-08
You are getting DNS server (your router) from DHCP, I think.

---

