---
title: "Blocking web-site"
date: 2011-12-15
forum: General Help
---

### Post by nickyflavian on 2011-12-15
I'm trying to block a website and all his subdomains , let's say yahoo.com, and I configured the squid.conf like this : dstdom_regex block ".yahoo.com" and then http_access deny block.And of course I restarted the daemon. But it doesn't work . What I am doing wrong? I was thinking that it doesn't work because I don't setup a hostname proxy or sth like that? So could anybody give me some tips ? Thanks

---

### Post by jamesisin on 2011-12-15
Should you be using a wildcard?

"*.yahoo.com"

---

