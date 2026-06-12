---
title: "Where to find primary &amp; secondary DNS?"
date: 2010-11-08
forum: General Help
---

### Post by GoldNinja on 2010-11-08
My question is that simple, **how can I find out what is my primary and secondary DNS?** I've tried commads: *$ cat /etc/resolvconf* and *less /etc/resolv.conf* but they didn't work. Also, when I open the resolv.conf file, it only says:

nameserver 192.168.100.1
domain Elisa
search Elisa

I really appreciate your help! :D

---

### Post by Sam on 2010-11-08
CLI way: grep ^nameserver /etc/resolv.conf

GUI way: Right click on the network indicator, "Connection Information"

---

### Post by skillet-thief on 2010-11-08
> **GoldNinja said:**
> 
nameserver 192.168.100.1
domain Elisa
search Elisa


192.168.100.1 is your primary DNS and it looks like you don't have a secondary.

---

### Post by QLee on 2010-11-08
[QUOTE=GoldNinja]My question is that simple, **how can I find out what is my primary and secondary DNS?** I've tried commads: *$ cat /etc/resolvconf* and *less /etc/resolv.conf* but they didn't work. Also, when I open the resolv.conf file, it only says:

nameserver 192.168.100.1
domain Elisa
search Elisa

I really appreciate your help! :D[/QUOTE]
Well, that looks like your network is using the router at 192.168.100.1 for DNS, if you have access to the router, you can check what it uses for DNS on the WAN side or if you are not authorised to access the router then you can ask your sys admin.

---

