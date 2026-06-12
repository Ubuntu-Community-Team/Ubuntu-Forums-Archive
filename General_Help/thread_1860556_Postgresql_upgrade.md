---
title: "Postgresql upgrade"
date: 2011-10-14
forum: General Help
---

### Post by mutley89 on 2011-10-14
Hi

Upgraded to 11.10 yesterday, and with it comes postgres 9.1, from 8.4.  What is the easiest way to restore my previous database with 9.1.  I have a file produced with pg_dump from 2 weeks ago, but would prefer to transfer the up to date version somehow.  Is it possible to access th e 8.4 created database from 9.1?

ETA: Some further googling shows that there is a perl script named "pg_upgradecluster" for this purpose however I can't figure out how to use it.  It gives: 
"Error: specified cluster is not running".  How do I allow it to connect to the 8.4 database?

ETA: Solved by temporarily reinstalling 8.4 then using the script mentioned above.

---

### Post by kongo09 on 2011-10-18
Great that you solved it.

Could you please elaborate a bit on how you did it. I'm totally lost right now. I've reinstalled **[FONT=Courier New]postgresql-8.4[/FONT]** but now what? I don't understand the **[FONT=Courier New]pg_upgradecluster[/FONT]** command.

---

### Post by kongo09 on 2011-10-18
Ok, now here is how I did it right after the 11.10 Ubuntu upgrade:

```

sudo apt-get install postgresql-8.4
sudo -u postgres pg_dropcluster 9.1 main --stop
sudo -u postgres pg_ctlcluster 8.4 main start
sudo -u postgres pg_upgradecluster 8.4 main
sudo -u postgres pg_dropcluster 8.4 main --stop
sudo apt-get remove postgresql-8.4

```

---

