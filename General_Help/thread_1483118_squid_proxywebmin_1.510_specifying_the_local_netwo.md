---
title: "squid proxy/webmin 1.510: specifying the local network allows everyting(?)"
date: 2010-05-14
forum: General Help
---

### Post by TechMansoor on 2010-05-14
I'm using webmin 1.510 to run squid. Every time I specify the network and allow it via proxy restrictions, it allows all sites to be accessed. 

I have denied everything else with the exception of my network and the allotted sites even though my clients are getting to any sites they want to.

What do I need to do to make squid work properly or in other words, **make my clients access only the allowed sites I have specified?**

---

### Post by TechMansoor on 2010-05-14
?anyone awesome linux community?

---

### Post by TechMansoor on 2010-05-17
> **TechMansoor said:**
> I'm using webmin 1.510 to run squid. Every time I specify the network and allow it via proxy restrictions, it allows all sites to be accessed. 

I have denied everything else with the exception of my network and the allotted sites even though my clients are getting to any sites they want to.

What do I need to do to make squid work properly or in other words, **make my clients access only the allowed sites I have specified?**


Still not solved awesome linux community..

It's all about proxy restrictions..whenever i allow 'localnet' which is my local network of 192.168.0.0, it basically gives access to all websites. Squid, within the webmin interface, is not allowing my specifiedsites only..i deny everything except 'localnet', 'allowedsites', and 'safeports'. If i deny safeports no client go anywhere. If i deny localnet no one can get anywhere. But when I allow them both, all clients are allowed access to the internet..

What am I doing wrong? How do I just merely setup squid where my clients can only access my allowed sites????????

---

