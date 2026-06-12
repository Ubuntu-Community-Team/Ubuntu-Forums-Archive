---
title: "mysql-admin in Ubuntu 12.04"
date: 2012-05-02
forum: General Help
---

### Post by xtgyal on 2012-05-02
When my Ubuntu upgraded from 11 to 12, it seems to have uninstalled mysql-admin and removed it from the Ubuntu Software Center.  I found it listed in Synaptic, but it won't let me install and gives the following error: 

mysql-admin:

Package mysql-admin has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

What happened to mysql-admin and how do I get it back??

---

### Post by miksa007 on 2012-05-03
apt-get install mysql-workbench

---

### Post by xtgyal on 2012-05-03
Thanks, mysql-workbench works.  I really miss mysql-admin though, why was it removed from the repository?  Is there another way to get it back?

---

### Post by Cheesemill on 2012-05-03
MySQL Administrator was anounced EOL (End Of Life) on December 2009, and as such is no longer being developed or supported.

All users are advised to switch to MySQL Workbench instead.

[http://dev.mysql.com/support/eol-notice.html](http://dev.mysql.com/support/eol-notice.html)

---

### Post by Dngrsone on 2012-05-03
I find [phpMyAdmin](https://help.ubuntu.com/community/phpMyAdmin) easier to work with; but then, I am only administering a local blog database.

---

### Post by xtgyal on 2012-05-05
Thanks for the info, and yeah that is my situation as well, I'm not familiar with the ins and outs of MySQL; I only use it for backing up MediaWiki and other MySQL-based web applications.  MySQL Workbench has more features than I need or understand how to use, I found MySQL Administrator's interface much simpler and easier to use.  Would be helpful if perhaps the developers could make a "MySQL Workbench Lite" with just basic features like backup and restore for users not familiar with MySQL.  I'll check PHPMyAdmin though, I think I may have used that too some point in the past.

---

### Post by Cheesemill on 2012-05-05
If you're only after a backup solution then take a look at automysqlbackup in the repositories.

You just need to edit a simple text file (/etc/defaults/automysqlbackup) to add the details of your MySQL server and run the command daily from crontab.

From the website:

AutoMySQLBackup with a basic configuration will create Daily, Weekly and  Monthly backups of one or more of your MySQL databases from one or more  of your MySQL servers.

Other Features include:
- Email notification of backups
- Backup Compression and Encryption
- Configurable backup rotation
- Incremental database backups

---

