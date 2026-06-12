---
title: "IP alias down after several time"
date: 2010-12-08
forum: General Help
---

### Post by mc_scRAT on 2010-12-08
Hi, Community People.
I've got strange behaviour: my wlan0's IP is given by DHCP server. I got an IP alias on it, that is listened by dhcpd server and got routing from my wlan clients via this IP alias to Internet via wlan0 :KS
The case is that after some time an alias is down - and I've to manually up it. I got an auto-up on-boot script, got auto-up script on resume/thaw (after suspend/hibernate), and my netbook is up 24/7... So I dunno what happens - no clues seen in dmesg, syslog or whatever.
The most strange is when I try to connect via a client, when an alias is already down: client earns right IP address, but no internet connection is available...
Please, help me guess what's going in inside and fix this issue.

---

