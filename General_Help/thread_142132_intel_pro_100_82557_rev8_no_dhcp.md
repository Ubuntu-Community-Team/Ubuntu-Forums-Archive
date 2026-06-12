---
title: "intel pro 100 82557 rev8 no dhcp"
date: 2006-03-09
forum: General Help
---

### Post by dmizer on 2006-03-09
reopen a previously addressed issue, unresolved:
[http://ubuntuforums.org/archive/index.php/t-11855.html](http://ubuntuforums.org/archive/index.php/t-11855.html)

don't much care for the idea of running to gentoo for the fix on this as i've gone through more than a fair share of install cd burning to arrive at ubuntu.

the card shows in network manager, i can activate it, but it won't pull an ip from my dhcp.  i've attempted to statically assign an ip, but that still wouldn't allow the machine to get online.  if i set the card to dhcp and activate the card, the network manager shows the card as active, but if i shutdown the network manager and restart, the card shows as not active.

dmesg does show e100 is loaded.

once again, google had been fruitless.  i need this machine for work, and i need it to be able to get online.

edit to add:
i have attempted to disable ipv6 according to this [wiki]("https://wiki.ubuntu.com/WebBrowsingSlowIPv6IPv4?highlight=%28ipv6%29") but the hosts tab in network settings still shows ip6 for the aliases.

---

### Post by dmizer on 2006-03-10
lsmod no longer lists ipv6.

anyone have any ideas on this at all?

---

