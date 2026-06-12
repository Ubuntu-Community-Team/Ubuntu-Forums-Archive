---
title: "Unable to connect to modem via ssh?"
date: 2010-11-01
forum: General Help
---

### Post by cAlpha on 2010-11-01
I've previously connected to my modem using telnet but am having difficulties connecting using ssh.  

I get the error: 
"ssh: connect to host 192.168.0.1 port 22: Connection refused"

when I try to connect to the modem via ssh.  

I DO have OpenSSH installed and I've also tried using the the login (-l) option to no avail.  

Any thoughts on what may be causing this difficulty?

---

### Post by dcstar on 2010-11-01
> **cAlpha said:**
> I've previously connected to my modem using telnet but am having difficulties connecting using ssh.  

I get the error: 
"ssh: connect to host 192.168.0.1 port 22: Connection refused"

when I try to connect to the modem via ssh.  

I DO have OpenSSH installed and I've also tried using the the login (-l) option to no avail.  

Any thoughts on what may be causing this difficulty?

SSH is a protocol that modems do not (generally) support. Use telnet.

---

### Post by cAlpha on 2010-11-01
> **dcstar said:**
> SSH is a protocol that modems do not (generally) support. Use telnet.

Thanks for your reply.  I'll just need to tolerate the lack of security associated with telnet then or is there a better way?

---

