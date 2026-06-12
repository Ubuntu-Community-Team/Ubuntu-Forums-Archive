---
title: "Iptables &amp; chains"
date: 2010-08-06
forum: General Help
---

### Post by Vtsedi on 2010-08-06
How would you remove all iptable rules and chains?

---

### Post by baguahsing on 2010-08-06
Here is the man page:  [http://manpages.ubuntu.com/manpages/lucid/man8/iptables.8.html](http://manpages.ubuntu.com/manpages/lucid/man8/iptables.8.html)
 
I am new at this myself but I believe if you type:
 
Code
iptables -F  
 
will flush all chains all in the table if no chain is specified.

---

### Post by The Cog on 2010-08-06
I think the following should cover it:
```
/sbin/iptables -F
/sbin/iptables -X
/sbin/iptables -t nat -F
/sbin/iptables -t nat -X
/sbin/ip6tables -F
/sbin/ip6tables -X
/sbin/iptables -P INPUT ACCEPT
/sbin/iptables -P OUTPUT ACCEPT
/sbin/iptables -P FORWARD ACCEPT
/sbin/ip6tables -P INPUT ACCEPT
/sbin/ip6tables -P OUTPUT ACCEPT
/sbin/ip6tables -P FORWARD ACCEPT
```

---

