---
title: "vnc server"
date: 2012-07-30
forum: General Help
---

### Post by spunkycabage11 on 2012-07-30
I managed to finally setup vnc server, and ssh tunnel into my ubuntu box but whenever i try to connect to localhost on my vnc client i get the error:  

channel 3: open failed: connect failed: Connection refused

I ran sufo ufw status to see if the firewall was blocking me access and i got the output 

Status:inactive.

The ssh tunnel command im using is ssh -p 22 epsilon -L 5900:localhost:5900

(epsilon is ssh username@192.168.0.10)

Thanks in advance.

---

