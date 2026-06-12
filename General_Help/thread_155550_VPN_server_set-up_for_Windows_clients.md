---
title: "VPN server set-up for Windows clients"
date: 2006-04-05
forum: General Help
---

### Post by ExemplarUbuntu on 2006-04-05
Can someone help clarify a few things for me ? I am trying to set-up Breezy to act as a VPN server for Windows clients.

I've read several articles and all seem to disagree about what software is needed and all seem to have gaps or make assumptions about the set-up.

Initially I want to connect across the LAN and access a partition/folder on the Ubuntu server. Eventually VPN will be opened for external access. All the clients have WinXp Pro.

What do I need to install on the Ubuntu server ? pptpd, OpenSwan, lp2p ??
I all ready have Samba working.

Peter

---

### Post by ExemplarUbuntu on 2006-04-07
bump

---

### Post by ExemplarUbuntu on 2006-04-11
Well without help I managed to get a pptp connection using Poptop
but this isn't very secure so I am now working with a very useful guide to
ipsec:

[http://www.natecarlson.com/linux/ipsec-x509.php](http://www.natecarlson.com/linux/ipsec-x509.php)

I am not totoally clear which ip addresses I should be using where but
I think it is almost working. The ipsec command on the WinXP box looks
to be connecting but when I try to ping the Ubuntu server it just tries
to negotiate and never succeeds so it looks like more fiddling is needed.

I hope this may be of help to someone else but if anyone knows of a
solution to my problem please let me know.

---

