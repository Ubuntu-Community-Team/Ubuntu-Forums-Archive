---
title: "Lampp error: &quot;Another mysql daemon is already running&quot;"
date: 2009-07-24
forum: General Help
---

### Post by deejay_99 on 2009-07-24
**Lampp error: "Another mysql daemon is already running"**        
     
 When I start lampp, (sudo /opt/lampp/lampp start)  I get the message "Another mysql daemon is already running"

I researched this and it seems that another mysql service is installed (by ubuntu?) and runs on ubuntu startup.

I can stop this daemon using:  sudo /etc/init.d/mysqld stop

After doing this, I can start lampp okay and everything seems fine.

My question is: How can I disable or remove this first "non lampp" sql from starting? Or, is it some other problem like file permissions or mysql authentication?

 I am a newbie so precise instructions are much appreciated.

Thanks

---

### Post by cariboo on 2009-07-24
Open and Applications-->Accessories-->Terminal and type:

```
update-rc.d -f mysql remove
```

This will stop the other instance of mysql you installed from starting.

---

### Post by deejay_99 on 2009-07-24
Thanks Cariboo ... that worked great!

Much appreciated,

deejay

---

### Post by yanto85 on 2010-08-24
i have do as up there.. but daemon still running...
what must i do... please..! i have do reboot.

---

