---
title: "dns not working - need help"
date: 2006-04-13
forum: General Help
---

### Post by Goonie on 2006-04-13
Hi all

I can't ping any machines on my network by hostname, only by their IP address. This includes localhost

What could be the problem?

Thx 
Goonie

---

### Post by rabidphage on 2006-04-13
[https://launchpad.net/distros/ubuntu/+source/dhcp3/+bug/31057](https://launchpad.net/distros/ubuntu/+source/dhcp3/+bug/31057)
might help

---

### Post by Goonie on 2006-04-14
Interesting bug but not what I'm dealing with :( My resolv.conf is fine and the nameservers work in the sense that I can resolve names on the internet but not on my local net. And I don't have the resolvconf package installed.

Goonie

---

### Post by timfrost on 2006-04-14
What does /etc/nsswitch.conf have for hosts?

I have 
hosts:          files dns

and I can talk to other hosts on the LAN, using the names in /etc/hosts.
For localhost, complain to your ISP that they don't have a localhost DNS entry.

Or change your nsswitch.conf, and add an entry to /etc/hosts:
127.0.0.1 localhost.localdomain localhost

---

