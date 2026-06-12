---
title: "Running phpmyadmin"
date: 2009-08-24
forum: General Help
---

### Post by gandalf458 on 2009-08-24
I've got phpMyAdmin installed but I don't need to access it very often so I forget. I thought I accessed it at [http://localhost/phpmyadmin/](http://localhost/phpmyadmin/) however although I get in to phpMyAdmin this way it doesn't list my databases - the only database listed is information_schema. I have two dbs both of which are working.

Any ideas what I'm missing? Thanks

---

### Post by DaithiF on 2009-08-24
are you logging to phpmyadmin as the mysql root user, or as a user which has access to your databases?

---

### Post by gandalf458 on 2009-08-24
Ah! Believe it or not I was logging in as a user who does NOT have access to the databases! Looking at my PHP code I see the databases belong to root.

Many thanks for pointing me in the right direction...

---

