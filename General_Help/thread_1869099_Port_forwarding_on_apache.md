---
title: "Port forwarding on apache"
date: 2011-10-25
forum: General Help
---

### Post by thkalam on 2011-10-25
Hello guys

I m new here and new to ubuntu

I need help... I allready have installed ubuntu server with apache, php, mysql, phpmyadmin installed

I want to access from another pc outside my network ubuntu' s web services. 

I ve logged in to my router and i managed to forwared port 9414 for ubuntu' s server ip

Then i tried to change apaches default ip 80 to 9415 but nothing happened.

Any suggestions?

---

### Post by SeijiSensei on 2011-10-25
Forward the port to the Apache server's port 80.  Most routers allow you to forward a port to some arbitrary port on the target machine.

---

### Post by prodigy_ on 2011-10-25
> **thkalam said:**
> nothing happened

It can be anything. Apache config (not bound to the IP from which you're trying to forward?), routing (wrong default route somewhere?), forwarding (mixed up local and remote ports?), misconfigured firewall, etc.

For diagnostics try to forward a known working port. E.g. TCP/22, if you have SSH up and listening on this port. Then try to telnet from behind the router. If SSH answers, then you got port forwarding and routing right and the problem is caused by something else.

---

