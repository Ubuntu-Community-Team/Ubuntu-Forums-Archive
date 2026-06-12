---
title: "How to close port 8090?"
date: 2011-06-01
forum: General Help
---

### Post by chuawenching on 2011-06-01
Hi everyone,

I am using Ubuntu 10.04 LTS server 32 bits.

I already installed nginx to listen to port 80. Nginx will route all traffic to [http://127.0.0.1:8090](http://127.0.0.1:8090) (apache2).

So when i type [www.company.com](www.company.com), it will direct to the right website. Nginx and apache2 working fine here.

But  the problem here is if i type in [www.company.com:8090](www.company.com:8090), I can still  access from the web browser. How can I prevent people accessing via  individual ports?

I notice nmap 127.0.0.1, port 8090 is open (as i set that in apache2 ports.conf to listen 127.0.0.1:8090).

What  can I do to block this port 8090 to be accessible by outside request  without affecting my apache or nginx? Does IPTables play a role here? If  yes, any way to get around with this?

Any help? Thanks.

---

