---
title: "Help with reverse proxy setup"
date: 2011-04-13
forum: General Help
---

### Post by hamhead69 on 2011-04-13
First off let me state that I am a complete newbie to Ubuntu. Here is my dilema. I'm trying to pass multiple dpmains thru one ubuntu server to various hosts on my local network.
 
[http://w](http://w)[ww.domain1.com]("http://www.domain1.com") should be sent to the /var/www folder on the local host.
 
[https://www.domain2.com](https://www.domain2.com) should be forwarded to an IIS box on my local network (owa.nunya.local)
 
[https://www.domain3.com](https://www.domain3.com) should be sent to another ubunto box on my local network (smtp.biznet.net)
 
I have tried placing VirtualHost entries in /etc/apache2/sites-available/default and [http://www.domain1.com](http://www.domain1.com) and [https://www.domain2.com](https://www.domain2.com) both work but [https://www.domain3.com](https://www.domain3.com) gets forwarded to the c:\inet\pub folder on the IIS box.

---

### Post by hamhead69 on 2011-04-18
Anyone?

---

### Post by hamhead69 on 2011-06-15
Can anyone help me to resolve this issue? :(

---

