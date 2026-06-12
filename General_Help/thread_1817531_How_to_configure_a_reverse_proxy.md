---
title: "How to configure a reverse proxy"
date: 2011-08-03
forum: General Help
---

### Post by AsmodeusRimmon on 2011-08-03
Hello, I'm not sure if this is where I post this, if it's not please forgive me.

I've set up a reverse proxy on my home server that looks like this:

ProxyRequests off
      ProxyPreserveHost on
      <proxy *>
      Order deny,allow
      Allow from all
      </proxy>
ProxyPass / [http://www.*.us/](http://www.*.us/)
ProxyPassReverse / [http://www.*.us/](http://www.*.us/)

(I've tried it with and without the www)

My home sever has a *.dyndns.org domain name.

When I go to *.dyndns.org I get an error saying:

The website you are trying to access could not be located on this server. If
you are trying to visit the secure (https) version of this website, please
retype the URL without https.

What am I doing wrong?

---

