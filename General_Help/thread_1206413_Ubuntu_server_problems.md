---
title: "Ubuntu server problems"
date: 2009-07-07
forum: General Help
---

### Post by ftaylor on 2009-07-07
Hello,

I just bought a VPS with Ubuntu server on it. It has a default configuration of LAMP. I can ping and ssh to the server, and I have set my domain name's A entry to the server ip address. Whenever I type the domain name or the server IP in the address bar, I get connection refused. What do I need to configure for this to work?

/var/log/apache2/access.log is empty - so my requests don't even seem to be making it to apache.

Thanks,
Finbarr

---

### Post by alphacrucis2 on 2009-07-07
> **ftaylor said:**
> Hello,

I just bought a VPS with Ubuntu server on it. It has a default configuration of LAMP. I can ping and ssh to the server, and I have set my domain name's A entry to the server ip address. Whenever I type the domain name or the server IP in the address bar, I get connection refused. What do I need to configure for this to work?

/var/log/apache2/access.log is empty - so my requests don't even seem to be making it to apache.

Thanks,
Finbarr

Connection refused might mean that apache isn't actually running. 

```
sudo service apache2 start
```

---

