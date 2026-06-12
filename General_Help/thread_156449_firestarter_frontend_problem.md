---
title: "firestarter frontend problem"
date: 2006-04-07
forum: General Help
---

### Post by placide on 2006-04-07
I use **firestarter** for internet access sharing and it worhs fine. When the computer boots, it loads firestarter service and everything works (Internet sharing).

The problem is when I start the frontend with: 

[FONT="Courier New"]sudo firestarter[/FONT]

**the internet sharing stops to work** (just start it and nothing else more!)

I even tried to close the the frontend and restart firestarter service with:
[FONT="Courier New"]sudo /etc/init.d/firestarter restart[/FONT]
It restarts but no Internet sharing until reboot the computer!!!

When I start firestarter I get these messages

[FONT="Courier New"]Try `iptables -h' or 'iptables --help' for more information.
Bad argument `194.65.100.117'
Try `iptables -h' or 'iptables --help' for more information.
Bad argument `194.65.100.117'
Try `iptables -h' or 'iptables --help' for more information.
Bad argument `INBOUND'
Try `iptables -h' or 'iptables --help' for more information.
Bad argument `INBOUND'
iptables v1.3.3: host/network `' not found
Try `iptables -h' or 'iptables --help' for more information.
iptables v1.3.3: host/network `' not found
Try `iptables -h' or 'iptables --help' for more information.
Firewall started[/FONT]

---

### Post by mlind on 2006-04-07
does firestarter have any configurable settings regarding to internet sharing?

---

### Post by Ramses de Norre on 2006-04-07
Preferences > firewall > network settings there's a box for internet sharing, but I doubt that's your problem.
It looks like your iptables are badly set..

---

### Post by mlind on 2006-04-07
[QUOTE=Ramses de Norre]Preferences > firewall > network settings there's a box for internet sharing, but I doubt that's your problem.
It looks like your iptables are badly set..[/QUOTE]

firestarter *should* configure iptables correctly.

@placide
from firestarter GUI select Edit > Preferences > Firewall > Network Settings
enable "internet connection sharing" checkbox and confirm changes.

what does *sudo iptables -L* display after this?

---

