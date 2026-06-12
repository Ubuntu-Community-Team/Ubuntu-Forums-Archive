---
title: "UFW and tftp rule"
date: 2010-03-25
forum: General Help
---

### Post by uncle-c on 2010-03-25
Hi,
I'm trying to put / get files a machine running a tftp server but with no success . The client machine is behind a firewall and this is cause of the problem as when the firewall is disabled I can transfer files.

I've tried to add this rule but the firewall still blocks the transfer.

```
uncle@ubuntu:/test-$ sudo ufw  allow proto udp from 192.168.0.99 port 69
Rule added
unclec@ubuntu:/test-$ sudo ufw status
Status: loaded

To                         Action  From
--                         ------  ----
( Rules left out )

Anywhere                   ALLOW   192.168.0.99 69/udp

unclec@ubuntu:/test-$ 


```

I have also tried
 ```
sudo ufw  allow proto udp from 192.168.0.99 port 69 to 192.168.0.98 
```

(192.168.0.98 is the IP of the firewalled client 
192.168.0.99 is the IP of the tftp server)

but to no avail.

Any cures ?

TIA
C

---

### Post by gmargo on 2010-03-25
The tftp server does not send data to port 69.  The tftp server listens for new connections on port 69, and when it replies to the client, chooses a new port for the connection. The tftp conversation (after the initial packet) takes place over a pair of non-69 ports, one on each side.  As long as you are allowing the client to call out to the server on port 69, the "ESTABLISHED" state should take care of the rest of the udp "connection".

---

