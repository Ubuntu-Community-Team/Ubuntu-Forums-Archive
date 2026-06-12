---
title: "access windows partition with apache"
date: 2010-06-02
forum: General Help
---

### Post by chamalsl on 2010-06-02
Hi,

I mounted my windows partition(NTFS) using places menu in ubuntu.
It is mounted with my user (chamal).

I have also configured apache to host files in a directory in windows partition.
But when I open web browser and visit my site it says
"You don't have permission to access /MyWebSite/database.html on this server"

This is the output for "ls -l database.html".

-rwxrwxrwx 1 chamal chamal 1002 2010-05-29 21:11 database.html

This is the output for "ls -l database" (database is the folder containing database.html).
drwx------ 1 chamal chamal   0 2010-05-31 22:15 database

This is the output for "sudo -u www-data cat database.html"
cat: database.html: Permission denied

How can I give permission to apache to read files in my windows partition.

Thanks,
Chamal.

---

