---
title: "Mysql database move - troubleshooting"
date: 2009-07-28
forum: General Help
---

### Post by P0rridge on 2009-07-28
In order to move a Mysql database I have
- copied directory (and all files contained within - from maybe 15 tables) from default location /var/lib/mysql/DBNAME to /new dir/DBNAME
- created a link in /var/lib/mysql/DBNAME to /new dir/DBNAME
- changed the permissions of /new dir/DBNAME, its files and the link to read and write for all users
- restarted mysql

Problems include:
- 0 tables showing in the DBNAME database
- cant create a new table in the DBNAME database - get " MySQL said: Documentation
#1005 - Can't create table 'zzz' (errno: 13)"

Am running Ubuntu within VirtualBox. The new directory is in a second drive, which has been formated and mounted, seems to be working fine.

Oh the pain (and the waisted hours).

Any suggestions as to cause?

---

### Post by trwww on 2009-07-28
Your best bet is to use mysqldump.

---

### Post by DaithiF on 2009-07-29
agreed -- mysqldump is the recommended way to do this.  the command is simple:

mysqldump -h host -u user -ppassword --databases databasename  >  mydatabase.dump

then on the new server:
mysql -h newhost -u user -ppassword < mydatabase.dump

easy!  :)

---

