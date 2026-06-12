---
title: "Can anybody help me get this one to work?"
date: 2009-09-28
forum: General Help
---

### Post by choizy on 2009-09-28
Hello,

I am trying to create my own captive portal and I found an example I wanted to start with. I just can't figure out how to fix the line below. Any help would be appreciated.

Axel


choizy@ECCaptivePortal:~$ 

sudo awk 'BEGIN { FS="\t"; } { system("$IPTABLES -t nat -A internet -m mac --mac-source "$2" -j RETURN"); }' /var/lib/users

/bin/sh: -t: not found

---

