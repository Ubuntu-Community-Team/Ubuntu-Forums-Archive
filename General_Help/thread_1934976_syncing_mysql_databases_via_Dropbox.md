---
title: "syncing mysql databases via Dropbox"
date: 2012-03-03
forum: General Help
---

### Post by yanvolking on 2012-03-03
Hello community,

I use various computers some physical others virtual.  All share a common Dropbox folder for syncing.  I used to have a Libreoffice database in the Dropbox folder (which of course was synced across all my computers linked to Dropbox.  I have now migrated my Libreoffice databases to MySQL and would like to sync in the same way with all my computers.  I have tried doing this by moving the Mysql database folder to the Dropbox folder and then creating a symbolic link back from the Dropbox Mysql folder to the path where the original MySQL database folder was.

Path of MySQL database folder : /var/lib/mysql
Path of Dropbox database folder :  /home/yan/Dropbox/mysql

When I go to the mysql database folder I can see the Symlinked mysql folder and all the tables inside it (exactly the same as the Mysql folder in the Dropbox folder). 

But when I open a MySQL session, no database is detected.  If, however I move the Mysql folder from Dropbox back to /var/lib/, then the databases are detected.

It seems that a simlinked folder is not being detected by MySQL.

I did this symlink operation with the Mysql and Apache2 servers switched off as suggested in the numerous forum links on the subject, but this still does not give a positive result.

Any ideas what is going wrong?  Is there another way of syncing mysql databases across various computers?

Thanks

---

