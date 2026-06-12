---
title: "Apache Subdomains and multiple named domains"
date: 2006-04-07
forum: General Help
---

### Post by Ported on 2006-04-07
Hi,

I have been searching and messing around trying to do this for ages! If someone can help me please.

I am trying to have my Kubuntu server host two domains: ported.dnsalias.com and chrystall.co.nz.

I also want to set up subdomain.chrystall.co.nz.

I have made the following files in /etc/apache2/sites-available/: chrystall.co.nz ported.dnsalias.co.nz and subdomain.chrystall.co.nz

I then symlink from /etc/apache2/sites-enabled/ to each of these.

I can see [www.chrystall.co.nz](www.chrystall.co.nz), chrystall.co.nz, and ported.dnsalias.com from a machine external to my local network. But I can not get subdomain.chrystall.co.nz to work.

My network is an ADSL Router with port 80 forwarded to my Kubuntu server.

Can anyone help?

---

### Post by Neeko on 2006-04-17
Subdomains are handled by the virtual hosts entry in Apache's config file.

Something like this I would imagine:
```
<VirtualHost *>
  ServerName subdomain.chrystall.co.nz
  DocumentRoot /<path to the htdocs>/subdomain/
</VirtualHost>
```

---

