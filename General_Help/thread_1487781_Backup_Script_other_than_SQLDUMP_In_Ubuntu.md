---
title: "Backup Script other than SQLDUMP In Ubuntu"
date: 2010-05-19
forum: General Help
---

### Post by Executionher on 2010-05-19
Hi I was wondering if it is possible to create a script in Ubuntu that will backup MYSQL databases without using MYSQL Dump. Since MYSQL Dump keeps crashes the Ad delivery on our servers. Can anyone Provide any info on this? It would be supper awsum if There is a way. :-) Thanks a million in advance.

---

### Post by apjone on 2010-05-19
To be honest I am unsure. Here is list of utilities via apt that may be worth looking into.

apt-cache search mysql | grep backup
bacula-common-mysql - network backup, recovery and verification - MySQL common files
bacula-director-mysql - network backup, recovery and verification - MySQL storage for Director
bacula-sd-mysql - network backup, recovery and verification - MySQL SD tools
automysqlbackup - a daily, weekly and monthly backup for your MySQL database
backup-manager - command-line backup tool
backupninja - lightweight, extensible meta-backup system
cedar-backup2 - local and remote backups to CD or DVD media
cedar-backup2-doc - local and remote backups to CD or DVD media (documentation)
mylvmbackup - quickly creating backups of MySQL server's data files
vbackup - A modular backup utility
arkpmysql - Enterprise network backup

---

