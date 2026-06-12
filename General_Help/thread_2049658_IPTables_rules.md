---
title: "IPTables rules"
date: 2012-08-29
forum: General Help
---

### Post by hhaydoura on 2012-08-29
I'm working on a virtual machine, i wrote this to block all ports except 555 and 443 :    {{{{ $ sudo iptables -A INPUT -i eth0 -p tcp --dport 555 -j ACCEPT   - $ sudo iptables -A INPUT -i eth0 -p tcp --dport 443 -j ACCEPT   - $ sudo iptables-save   }}}} then I went to /etc/network/interfaces   and wrote this as comment: {{{  pre-up iptables-restore < /etc/iptables.rules }}} +++  right now i'm having a problem removing these rules, I tried     {{{{ $ sudo iptables -D INPUT -i eth0 -p tcp --dport 555 -j ACCEPT $ sudo iptables -D INPUT -i eth0 -p tcp --dport 443 -j ACCEPT   $ sudo iptables-save  }}}}  but it is not giving me the right output i'm waiting for, anyone can help me in this ?

---

### Post by lisati on 2012-08-29
If you've found a solution, it might be of value to other users with similar problems if you post your solution and then mark the thread "solved."

---

