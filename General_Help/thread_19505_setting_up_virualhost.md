---
title: "setting up virualhost"
date: 2005-03-12
forum: General Help
---

### Post by tch647 on 2005-03-12
newbie can anyone advise me on how to add virual host A.com an B.com to apache2. Was using Fedora. Setup was easy, don't understand Ubuntu apache settings.

---

### Post by az on 2005-03-12
/etc/apache2/sites-available and /etc/apache2/sites-enabled

You configure your site by adding a file in avaiable and symlink it to enabled.

---

