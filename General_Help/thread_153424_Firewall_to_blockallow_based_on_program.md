---
title: "Firewall to block/allow based on program?"
date: 2006-03-31
forum: General Help
---

### Post by Kevinator on 2006-03-31
As far as I know, iptables can affect various ports, protocols, and packets but has no idea which program is sending or receiving a given packet. Is there a way to create filters based on the source or destination program?

---

### Post by Zelut on 2006-04-01
Have you tried Firestarter?  Its a super-simple firewall program with very easy to setup rules.  I don't recall if it will recognize per-program, but it might be close enough that you can set the ports you want.

---

### Post by cwaldbieser on 2006-04-01
[QUOTE=Kevinator]As far as I know, iptables can affect various ports, protocols, and packets but has no idea which program is sending or receiving a given packet. Is there a way to create filters based on the source or destination program?[/QUOTE]
iptables has an owner match module that lets you match packets in the OUTPUT chain based on the command issued, the uid, the gid, etc.

There are probably ways to subvert that kind of match, but depending on the purpose for the filter, it could be useful.

---

### Post by PriceChild on 2006-04-01
[quote=kuyaedz]Have you tried Firestarter? Its a super-simple firewall program with very easy to setup rules. I don't recall if it will recognize per-program, but it might be close enough that you can set the ports you want.[/quote]
 
It does recognise per program, as i see "gaim" "bittorrent" etc. Which you can disable when you want.
 
However, most things outbound are allowed by default.

---

