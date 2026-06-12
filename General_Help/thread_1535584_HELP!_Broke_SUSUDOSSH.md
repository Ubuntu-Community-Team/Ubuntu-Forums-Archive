---
title: "HELP! Broke SU/SUDO/SSH"
date: 2010-07-21
forum: General Help
---

### Post by metroid9824 on 2010-07-21
Hello,

So I really screwed up and just ran the command sudo chown -R wronguser /
 
Now everything is owned by the wrong user, and since then sudo and su is  broken. Whenever I sudo I get: sudo: must be setuid root. and when I su  into root, I get authentication failed. When I try to ssh into the  server I get "ssh_exchange_identification: Connection closed by remote  host".
 I don't have access to the physical machine because I am out of town,  and wont be able to reinstall ubuntu. So what should I do?


-Will

---

### Post by anglican on 2010-07-21
> **metroid9824 said:**
> Hello,

So I really screwed up and just ran the command sudo chown -R wronguser /
 
Now everything is owned by the wrong user, and since then sudo and su is  broken. Whenever I sudo I get: sudo: must be setuid root. and when I su  into root, I get authentication failed. When I try to ssh into the  server I get "ssh_exchange_identification: Connection closed by remote  host".
 I don't have access to the physical machine because I am out of town,  and wont be able to reinstall ubuntu. So what should I do?


-Will
Quite honestly I'd consider re-installing completely when you have access to the machine. Changing owner of absolutely everything will cause a lot of problems - not everything belongs to "root" and it's impossible to go back and set correct ownership to every file that you've changed. Chalk this one up to "experience" and be very careful with sudo in future (not to mention using commands recursively and doing **anything** to /).

If you really want to waste a lot of time trying to change ownerships back, you could try booting from a live CD (again when you have access to the machine).

H

---

