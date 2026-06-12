---
title: "Port 8080 Tomcat not receiving connections from other machines"
date: 2012-03-20
forum: General Help
---

### Post by sbatra on 2012-03-20
I have Tomcat running on port 8080.  I can connect to the tomcat webserver from localhost but not from other machines.  From localhost:
telnet xx.ucsf.edu 8080
Trying 169.230.xx.xx...
Connected to xx.ucsf.edu.
Escape character is '^]'.

From another machine, here is what I get:
nc -v xx.ucsf.edu 8080
nc: connect to xx.ucsf.edu port 8080 (tcp) failed: Connection refused

From the other machine, this works fine:
nc -v xx.ucsf.edu 22
Connection to xx.ucsf.edu 22 port [tcp/ssh] succeeded!
SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu7

No firewall is running (including ufw) .  See below.
sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination     

Any ideas?
Thanks, Saj

---

