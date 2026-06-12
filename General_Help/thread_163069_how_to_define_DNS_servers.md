---
title: "how to define DNS servers"
date: 2006-04-20
forum: General Help
---

### Post by jeisma on 2006-04-20
hello!

if you have two dns servers (primary secondary). how do you define them in the system?

in /etc/network/interfaces i have dns-nameservers parameter with a value, what about the secondary?

what does /etc/resolv.conf do?


thanks!

---

### Post by krusbjorn on 2006-04-20
Try System->Administration->Networking, then click the DNS tab.

---

### Post by dg_w on 2006-04-20
As krusbjorn said ... You can put both of them in there..
That will write them into the /etc/resolv.conf

Or you could edit it by hand with

sudo gedit /etc/resolv.conf

Mine simply reads
nameserver 10.0.0.1
nameserver 158.152.1.43

The only entry I have in there is the adsl router and an external DNS

:)

---

