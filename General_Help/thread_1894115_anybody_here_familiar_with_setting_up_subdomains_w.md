---
title: "anybody here familiar with setting up subdomains with dot.tk?"
date: 2011-12-11
forum: General Help
---

### Post by sirspazzolot on 2011-12-11
for example, I have mydomain.tk/transmission going to a transmission webui. I'd like to get tor.mydomain.tk to go to said webui as well.

I have 2 A record, [www.mydomain.tk](www.mydomain.tk) and mydomain.tk, pointing to my IP. accessing mydomain.tk works fine.

I guess I don't understand how to add a CNAME record. The following entries all make dot.tk yell at me but they won't tell me what's wrong and nothing on google has helped.
```

Hostname        |IP Address
tor.mydomain.tk |my.ip.addr.ess:43434
tor             |my.ip.addr.ess:43434
tor.mydomain.tk |mydomain.tk/transmission
tor             |mydomain.tk/transmission
```

it doesn't seem to like the idea of me specifying ports or certain directories.

---

