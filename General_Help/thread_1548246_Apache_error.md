---
title: "Apache error"
date: 2010-08-08
forum: General Help
---

### Post by cackles on 2010-08-08
```
apache2: Syntax error on line 281 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/all.scrapping.conf: No such file or directory
   ...fail!
```

Ive been trying to setup a couple of vhosts for the past few hours and now Im getting that error. I deleted the file, not for the first time, but I must have changed something and I cant see what it is this time. I purged apache and installed again about 5 times now with this error, deleting worked before but I just dunno what it is.

Great, now its coming up with a different file, the one I used after it when I sudo /etc/init.d/apache2 reload

apache2: Syntax error on line 281 of /etc/apache2/apache2.conf: Could not open configuration file /etc/apache2/sites-enabled/scrap.conf: No such file or directory
   ...fail!

I thought it was supposed to ignore these files if deleted?

---

