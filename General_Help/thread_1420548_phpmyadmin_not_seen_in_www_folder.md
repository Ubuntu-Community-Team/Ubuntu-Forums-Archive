---
title: "phpmyadmin not seen in www folder"
date: 2010-03-03
forum: General Help
---

### Post by kapi on 2010-03-03
Hi there,

wondered why I never noticed but for a while now the phpmyadmin folder seems to be missing from the www folder.

It still works in local host, but I'm a bit perplexed as to where it has gone.

---

### Post by mcduck on 2010-03-03
It's not even supposed to be in that directory if you installed it from Ubuntu's package management.

It's installed elsewhere and simply configured in Apache's configuration files. (you can have web sites anywhere, not just in /var/www, if you just configure them in Apache).

---

### Post by kapi on 2010-03-03
Thanks

---

