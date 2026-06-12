---
title: "Wireless DHCP fails on open networks"
date: 2006-05-14
forum: General Help
---

### Post by rjray on 2006-05-14
It seems that when I try to connect to a wireless network that doesn't use encryption, it is unable to catch the DHCP lease offering. It works fine when connecting to a network that uses a key. But when I'm at a cafe or someplace that doesn't, then I can't get connected.

For example, the connection I am currently using works fine when I boot the laptop to Windows XP, and under Ubuntu I can *detect* the same network, but when I configure it to use the ESSID and no key it never comes up. When I try to bring it up manually (i.e., not using the network-config application), I see 5-6 messages indicating that it's sending the DHCPREQUEST messages, but not getting any DHCPOFFER in response. Or so it says-- like I said, the windows side of the machine connects just fine.

Any suggestions?

---

