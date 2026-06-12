---
title: "apache on ubuntu desktop"
date: 2009-12-15
forum: General Help
---

### Post by oospill on 2009-12-15
I'm wanting to install apache and php on my laptop running Ubuntu Desktop, so I can learn PHP.  is apache going to run at startup?  how can I keep it from doing that?? (I have no reason for a webserver except for learning PHP)

I hope that made sense.

thanks for any input!

---

### Post by dcstar on 2009-12-16
> **oospill said:**
> I'm wanting to install apache and php on my laptop running Ubuntu Desktop, so I can learn PHP.  is apache going to run at startup?  how can I keep it from doing that?? (I have no reason for a webserver except for learning PHP)

I hope that made sense.

thanks for any input!

Apache is a HTTP service that always runs (there is little point having it otherwise).

You can stop it auto-starting like any other service.

---

### Post by plusnplus on 2009-12-16
Hi oospill,

you can start/ stop it with:
sudo /etc/init.d/apache2 start
sudo /etc/init.d/apache2 stop

---

