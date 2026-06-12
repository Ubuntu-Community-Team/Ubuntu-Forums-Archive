---
title: "add port in ssh"
date: 2010-01-08
forum: General Help
---

### Post by cucuru on 2010-01-08
hello, I'm trying to add a new port in my ssh server (without remove 22), but it doesn't work:

In /etc/ssh/sshd_config:

> 

# What ports, IPs and protocols we listen for
Port 22
Port 4455



and save and restart:

> 
sudo /etc/init.d/ssh restart


Next I try (client side):

> 
ssh xx.xx.xx.xx:4455
ssh: Could not resolve hostname xx.xx.xx.xx:4455: Name or service not known


but with 22 it still works.

What could be the problem? 

Can be a problem that I execute ssh restart also as remote client?

Thank you. Regards.

---

### Post by cucuru on 2010-01-08
Hello again, I found the solution, I wasn't executing the correct intruction, it is:

> 

ssh -p 4455 xx.xx.xx.xx


Thank you.

Regards

---

