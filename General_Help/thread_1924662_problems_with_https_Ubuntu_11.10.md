---
title: "problems with https Ubuntu 11.10"
date: 2012-02-13
forum: General Help
---

### Post by mac1234mac on 2012-02-13
Hello!

I've got problem with setting up https on Ubuntu 11.10. I followed procedure presented at:
[http://charles.lescampeurs.org/2012/01/14/ubuntu-11-10-setting-up-apache2-and-ssl-with-self-signed-certificate](http://charles.lescampeurs.org/2012/01/14/ubuntu-11-10-setting-up-apache2-and-ssl-with-self-signed-certificate)
When I restart apache2 I get, only, warnings that the server cannot resolve name. But port 80 (http) works. But when I try to enter [https://my.domain.name](https://my.domain.name) I get "Exeeded time of connection". Is this the issue with firewall?. Perhaps with certificate (snakeoil)?. I have no idea what else I could do.

Thank You for answer,

Cheers,

Mac.

---

### Post by dino99 on 2012-02-13
try:

sudo apt-get install wicd

then log out/in to your session

---

