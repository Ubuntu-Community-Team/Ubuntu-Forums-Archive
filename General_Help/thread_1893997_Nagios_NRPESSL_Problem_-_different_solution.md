---
title: "Nagios NRPE/SSL Problem - different solution"
date: 2011-12-11
forum: General Help
---

### Post by draven76 on 2011-12-11
I was having the problem described in:

[http://ubuntuforums.org/showthread.php?t=875240&highlight=nrpe](http://ubuntuforums.org/showthread.php?t=875240&highlight=nrpe)

on my new ubuntu server 11.10 32 bit virtual machine.

To solve the problem I had to:

1) install libssl-dev
2) use the following command (different from the post linked above): sudo ./configure --with-ssl=/usr/bin/openssl --with-ssl-lib=/usr/lib/i386-linux-gnu/

Hope it helps others.

Dario

---

### Post by hackataca on 2012-01-20
It works. Thanks.

---

### Post by demetriades on 2012-09-14
Brilliant, this worked for me too. Thanks!

---

