---
title: "Web server not working"
date: 2010-12-12
forum: General Help
---

### Post by WeaponsTheyFear on 2010-12-12
Hello all,
I upgraded to Ubuntu 10, actually went with a fresh install. I used tasksel to install apache, php, mysql and phpmyadmin.  However, I cannot view my sites at all.  I enabled mod-rewrite with sudo a2enmod rewrite, restarted apache and still the rewrites didn't work.

I then tried going through the 000-default file to change allowoveride none to all, and for whatever reason all I see now is 403 forbidden errors on every page (even the main root directory, since my site is in a directory inside the root).

Loosing my mind trying to figure this out, never had problems like this before configuring and getting a local server to run.  Has anyone ran into this problem and can give a bit of assistance?

---

