---
title: "dansguardian"
date: 2011-05-30
forum: General Help
---

### Post by Rakeshvijayan on 2011-05-30
Hi friends I install dansguardian on my ubutu .and I started to configure dansguradian then  I stuck on the dansguardian restart command,  command is ""sudo /etc/init.d/dansguardian restart ""

result is " Error binding server socket :[8080](Address already in use)
Exiting with error    [fail]

---

### Post by sj1410 on 2011-05-30
some program is already using the port 8080, may be squid or a webserver. change filterport in /etc/dansguardian/dansguardian.conf

---

### Post by Rakeshvijayan on 2011-05-30
is it we have any option to find which package use this port and from the port filtering I change it to 8089 and do the restart command but no way .. fail message with out error ...

---

