---
title: "IPTables question."
date: 2006-01-22
forum: General Help
---

### Post by rensu on 2006-01-22
I have a pretty stupid question but does iptables close all ports automatecally? And I have to open them manualyly?
Like there is no rule about ports and then im adding this:
iptables -A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
Then is only open port 22 and other ports like 23 i can't use or i have to add a rule to close all ports.

---

### Post by rensu on 2006-01-24
Any help :S

---

### Post by Horndog on 2006-01-24
Most firewall type solutions have to open http and ftp ports at access the server. Why don't you install-run Firestarter from Synaptic? It's a front end GUI for iptables very easy to use. Unless, of course, you just have the minimal server install.

---

### Post by rensu on 2006-01-24
Im only able to use console.

---

