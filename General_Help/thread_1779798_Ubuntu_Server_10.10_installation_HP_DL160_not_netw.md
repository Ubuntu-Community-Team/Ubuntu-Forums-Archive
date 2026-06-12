---
title: "Ubuntu Server 10.10 installation HP DL160 not network card driver"
date: 2011-06-11
forum: General Help
---

### Post by kwinter on 2011-06-11
I just install Ubuntu Server 10.10 (image from ubuntu site [http://releases.ubuntu.com/maverick](http://releases.ubuntu.com/maverick) ,64-bit PC (AMD64) server install CD) in HP DL169 G6, but it can not recognize network card ,
specification: HP NC107i/NC362i

and HP have not officially support Ubuntu Server.

how can i resolve this problems?

help,thanks

---

### Post by wildmanne39 on 2011-06-11
> **kwinter said:**
> I just install Ubuntu Server 10.10 (image from ubuntu site [http://releases.ubuntu.com/maverick](http://releases.ubuntu.com/maverick) ,64-bit PC (AMD64) server install CD) in HP DL169 G6, but it can not recognize network card ,
specification: HP NC107i/NC362i

and HP have not officially support Ubuntu Server.

how can i resolve this problems?

help,thanks

Hi, run this command in a terminal
```
sudo lshw -c network
``` and post the outcome here.

---

