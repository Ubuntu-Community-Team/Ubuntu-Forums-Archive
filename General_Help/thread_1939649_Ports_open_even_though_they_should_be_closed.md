---
title: "Ports open even though they should be closed"
date: 2012-03-12
forum: General Help
---

### Post by mrchrister on 2012-03-12
Hey guys,

I don't understand whats going on with my rootserver...
I have reset iptables and just opened the port for ssh.
Now suddenly over night I see that there are a various of ports open:
21,80, 135, 139, 445, 3128

Could it be that vsftpd for example put rules in automatically to allow input on port 21?

I also tried disabling iptables with this command:

```
# iptables -X
# iptables -t nat -F
# iptables -t nat -X
# iptables -t mangle -F
# iptables -t mangle -X
# iptables -P INPUT ACCEPT
# iptables -P FORWARD ACCEPT
# iptables -P OUTPUT ACCEPT
```

after this i did a port scan with shields up! but still there seem to be rules I can not change. Most ports are still closed and the ones mentioned above are open...

I experimented with firestarter and ufw but uninstalled both... could it be that they still control the firewall?

services i have installed on my root server are ftp, openvpn, apache and vnc

---

### Post by HermanAB on 2012-03-12
Linux is not Windows.  Rather than trying to control services through a firewall, you should simply stop the services instead.

---

### Post by mrchrister on 2012-03-12
hey hermann i understand what you are saying, but how could I achieve to have no ports blocked? Even if I switch off iptables most ports are closed

This is just for testing purposes, I don't want to leave all ports unblocked...

---

