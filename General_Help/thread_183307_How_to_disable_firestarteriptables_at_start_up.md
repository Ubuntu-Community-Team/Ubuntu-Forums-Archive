---
title: "How to disable firestarter/iptables at start up?"
date: 2006-05-27
forum: General Help
---

### Post by Mitush on 2006-05-27
I have firestarter installed on my Breezy box. When the system boots up to the login screen, the firewall (iptables?) is apparently already up and running. The problem is that I am using VPN to connect to office network and it does not work with the firewall. So, in order to use VPN, I need to log into Gnome desktop, run firestarter and stop firewall from there. How can I disable firewall/firestarter on start up, without having to log into gnome?

---

### Post by user1397 on 2006-05-27
i would strongly recommend not to stop iptables, instead try to allow your vpn using firestarter (in firestarter, policy->outbound policy/inbound policy

---

### Post by Mitush on 2006-05-27
I may be mistaken, but it is not trivial to make VPN work with iptables/firestarter (using "policy" tab or otherwise). I tried that before without success. I think I also saw some thread where it was discussed and no obvious solution found.

Besides, the network sits behind NAT-enabled DSL modem, so no unauthorized inbound traffic gets to the hosts and the network itself is a "trust zone".

---

### Post by flaimo on 2006-06-29
i also would like to know, how to disable firestarter/iptaboles at startup.

---

### Post by foxystoatyweasely on 2007-03-20
Stopping your firewall is not a good idea as others have already said but if you really must do it, you could always run a cron job to shut it down and/or restart it. This is useful when you are testing your script and can prevent inadvertent lockouts.

Try this:
[http://www.iptablesrocks.org/guide/safetynet.php](http://www.iptablesrocks.org/guide/safetynet.php)

---

