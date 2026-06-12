---
title: "Postgresql won't start"
date: 2009-07-08
forum: General Help
---

### Post by namelessone on 2009-07-08
I recently recovered my server from a hard drive failure using a backup of my /etc directory.

After doing this, I am unable to start Postgresql anymore; I get an error that says:

> could not create lock file "/var/run/postgresql/.s.PGSQL.5432.lock": Permission denied

The file /var/run/postgresql is owned by user postgres, so I am unsure of why I would be getting this error message.

---

