---
title: "Restore Mysql data on EC2 karmic"
date: 2010-01-15
forum: General Help
---

### Post by edojan on 2010-01-15
hi folks, I am running a MySQL database on Karmic 
 with data directories sitting on attached EBS volume (i.e. /var/lib/mysql , /var/log/mysql and /etc/mysql are mounted to an attached EBS drive for persistent storage)
The EBS is mounted as /dev/sdh to /vol 
 
For backup purposes I use a second EBS volume (mounted to /vol1 
 as /dev/sdi) which stores daily mysqldump backup files. 
 

I am running a DR test trying to restore the database from the 
 backups. 

**Approach:**

I created a new EC2 instance from a saved image and attached 
 to it a new EBS volume created from a recent snapshot of the backup EBS
 volume. The idea is to start mysql and then restore the data using 



mysql> CREATE DATABASE IF NOT EXISTS db_name 
 mysql> use db_name ; 
 mysql> source db_name.sql ; 

 
**The Problem:**

The problem is that mysql doesn't start even after I run **mysql_install_db**  and also manually recreated the data directories.I also recreated the original password for 
 root@localhost and checked the phpmyadmin console but it shows 
 lot's of errors. Mysql server also fails to start. I am apparently 
 missing some important steps.

**Quesiton:**
What is the quickest way to recreate the system files (what else needs to run in addition to **mysql_install_db **so that I could proceed with the recovery? 
 

I am new to Mysql and your advice would be appreciated. 
 Thanks 
 Ed

---

