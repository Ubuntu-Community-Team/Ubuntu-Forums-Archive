---
title: "IP webcam monitoring??"
date: 2010-02-09
forum: General Help
---

### Post by rhynes on 2010-02-09
I've got a d-link dcs-920 and i'm trying to find a way to monitor/record via ubuntu 9.10 - or is it even possible. 

I installed zoneminder but it seems to want to use the default port of 80 and i've already got apache set up and running as a webserver and ports are forwarded. Is there a simple way to change the port for zoneminder?

Don't want to mess up my webserver cause of this - worse comes to worse i'll load an xp box for it. 

Is there another software available for ip cams?

Thanks.

---

### Post by spiderbatdad on 2010-02-09
Apache's NameVirtualHost directive is designed to serve multiple sites. Zoneminder config is done using apache as an interface. Just point apache to the necessary files in sites-enabled. As an example : [http://www.debian-administration.org/articles/412](http://www.debian-administration.org/articles/412)

---

