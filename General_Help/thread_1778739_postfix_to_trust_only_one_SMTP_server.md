---
title: "postfix to trust only one SMTP server"
date: 2011-06-09
forum: General Help
---

### Post by CNM on 2011-06-09
Hi ,

I have postfix relaying email to the internet for my LAN
I need to configure postfix to trust only one SMTP server to relay his emails to the internet
This is urgent please

Thanks

---

### Post by CNM on 2011-06-09
anyone ?

---

### Post by Seq on 2011-06-09
Sounds like you're looking for the relayhost parameter.

---

### Post by CNM on 2011-06-09
> **Seq said:**
> Sounds like you're looking for the relayhost parameter.

if i set mynetworks = 127.0.0.0/8 x.x.x.x/32
will postfix accept email comming from x.x.x.x and reject mails from others ?

---

### Post by _oOMOo_ on 2011-06-09
Yes the mynetworks parameter will work with x.x.x.x/32

---

