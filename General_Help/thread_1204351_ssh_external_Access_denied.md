---
title: "ssh external Access denied"
date: 2009-07-04
forum: General Help
---

### Post by Primefalcon on 2009-07-04
Ok this is what I've done

I've port forwarded port 60000 to my computer <192.168.1.100> which is static and assigned by physical addressing.

I've allows port 60000 traffic on my firestarter

I changed the SSH port in /etc/ssh/sshd_config to port 60000

I restarted the ssh server and even rebooted the computer

however trying to access this computer from an external network keeps telling me connection refused (it works from inside the network, just not from an external network)

Any suggestion?

---

### Post by Celauran on 2009-07-04
Just to be sure, you are passing port 60000 as a parameter when you call ssh, right?

---

### Post by Primefalcon on 2009-07-04
yeah

ssh -l brad <ip_address> -p 60000

and I also have both the internal and external ports forwarded, and the protocol on both

---

### Post by Primefalcon on 2009-07-04
NVM I worked out the issue, it was a known hosts issue, does this mean every-time I use a different hotspot, I'm going to have to clear the known_hosts file on both computers?

---

