---
title: "sql db"
date: 2011-05-30
forum: General Help
---

### Post by pyxel studio on 2011-05-30
Hi i need some help, i'm using a special software at work using winxp
mysql, phpmyadmin, apache.

I want to migrate to linux ubuntu,  i need to upload my sql DB file into
phpmyadmin using commands, how do i do that?

any tips.

---

### Post by katykat on 2011-05-30
First of all, I assume that on Win you are using WAMP or XAMPP. 

I found it very difficult to set up a stamdard LAMP server on Ubuntu, and the simplest way is to use the LAMPP program (google it) which installs itself in /opt. 

(You may need to reconfigure Apparmor or Selinux for it, or toggle them off). 

Part of the problems are a buggy version of Perl, and perennial problems with MySQL (in honesty not really noted in meerkat, but hell in Jaunty) - which are avoided with the LAMPP set up. 

LAMPP will install with a fully working Phpmyadmin. 

Back up the database from the Win machine, copy over to linux, and import it in Phpmyadmin. 
DO NOT try to copy the database files over. It wont work. 

Pay attention to the PHP versions also. If you are using 5.29 or earlier on the Win machine, with web sites such as OSCommerce, the newer 5.30+ versions will cause errors with deprecated functions (which can be fixed, but tedious). 

In MySQL you may also have to create the database you are importing first. Double check.

---

### Post by drdos2006 on 2011-05-30
Once you have your LAMP and server setup, the easiest way I found was to make a backup copy of the Windows sql database.

Copy the backup.sql file to an area on the server that you can access. ( I put mine in /var/www/sql-backup directory)

Create a blank database without tables with phpAdmin ( I use Webmin instead ).

From the server terminal I run :

mysql -u username -p ( for interactive password )  databasename < ( to import from ) /var/www/sql-backup/backupdatabase.sql

I enter the passowrd and the tables are imported.

regards

---

### Post by katykat on 2011-05-30
Its much easier just to use the import function in Phpmyadmin!

---

### Post by drdos2006 on 2011-05-30
Exactly, I was just spelling out the finer details.

regards

---

### Post by indytim on 2011-05-30
1.  Using your phpMyAdmin @ work:
a.  Export your table structure to a removable device
b.  Export your table contents also to a removable device, (note if your content is very large, you may want to break it up into smaller sized exports.

2.  On your Linux Lamp using phpMyAdmin:
a.  Set up your database.
b.  Mount your removable device from above.
c.  Using either the Import or SQL tab, first access your table structure file(s) and build into the database.
d.  Again using the Import or SQL tab navigate to the location for the table contents from above and build into the respective tables.

-DataMan

---

