---
title: "Get a compressed file from mysqldump"
date: 2010-07-13
forum: General Help
---

### Post by joshpennington on 2010-07-13
I would like to have my backup script that I am writing to create a sql dump of my database and go directly into a tar file.  Does anyone know how I could do this with one command?

To be more clear I would like to go from

mysqldump -u xxxx -pXXXXX tablename> currentbackup.sql
tar -czvf backup-XXXXXXXX.tgz currentbackup.sql
rm currentbackup.sql

To a single command somehow. Does anyone know how I could accomplish something like this?

Thanks

Josh Pennington

---

### Post by gsgleason on 2010-07-13
tar is an archive and is NOT compressed.  The compression comes from gzip or bzip2. It is therefore silly to put a single file in a tar (tape archive).  So, just compress it.

mysqldump -u xxxx -pXXXXX tablename|gzip > file.gz

Or you could do the same with bzip2.

---

### Post by joshpennington on 2010-07-13
That worked great. Thanks much.

---

