---
title: "Script to pull data from remote to local"
date: 2011-07-01
forum: General Help
---

### Post by geraldvillorente on 2011-07-01
Hi Guys,

I want to have a script that pull db from remote server to my local. Beside that the filename should contain current date the time the db was dumped.

Ex: **getdb databaseName**

Then the filename should be like this:

livedb-july012011.tar.gz
livedb-july022011.tar.gz

So basically I have an archive of DB. Similar to this I need also a script that pull directory from remote to my local.

Ex: **getdir htdocs**

Then the filename should be like this:

htdocs-july012011.tar.gz
htdocs-july022011.tar.gz
and so on...

Is this possible guys? Hope someone could shed some light.

Thanks

Gerald

---

### Post by SeijiSensei on 2011-07-01
[man rsync]("http://www.samba.org/ftp/rsync/rsync.html")

---

