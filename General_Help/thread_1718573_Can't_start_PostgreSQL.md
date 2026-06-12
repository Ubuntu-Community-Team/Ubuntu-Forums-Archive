---
title: "Can't start PostgreSQL"
date: 2011-03-31
forum: General Help
---

### Post by adamthompson on 2011-03-31
When I try to start PostgreSQL, I get the following error message: The PostgreSQL server failed to start. Please check the log output:
FATAL:  invalid value for parameter "lc_messages": "en_US.utf8"

I'm using Lucid 64-bit. Thanks.

---

### Post by SeijiSensei on 2011-03-31
Searching Google for that error brings up [this thread](http://postgresql.1045698.n5.nabble.com/ltree-installation-error-td2125133.html).

It looks like "sudo dpkg-reconfigure locales" might do the trick.  If locales aren't installed, you need to do that instead.

---

### Post by adamthompson on 2011-03-31
Thanks, that did do the trick. I had actually done a google search but didn't find that thread.

---

