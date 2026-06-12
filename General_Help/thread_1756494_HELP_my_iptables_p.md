---
title: "HELP my iptables :p"
date: 2011-05-12
forum: General Help
---

### Post by muzze22 on 2011-05-12
Hi, i currently have a VPS with UBUNTU 10.10, i want to use it for minecraft and maybe for other uses in the future. I once installed iptables with succes but this time it's giving me a hard time. everytime i apply my iptable it accepts minecraft but port 22 SSH is closed :( can anyone help me ? thx in advance
 
```
#!/bin/sh
#flush bestaande regels
iptables -F
iptables -X
# Policies
iptables -P INPUT DROP
iptables -P FORWARD DROP
iptables -P OUTPUT ACCEPT
# Alle looopback verkeer toelaten
iptables -A INPUT -i lo -j ACCEPT
iptables -A OUTPUT -o lo -j ACCEPT
#SSH toelaten
iptables -A INPUT -p tcp --dport 22 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 22 -j ACCEPT
#minecraft toelaten
iptables -A INPUT -p tcp --dport 25565 -j ACCEPT
iptables -A OUTPUT -p tcp --sport 25565 -j ACCEPT
```

---

