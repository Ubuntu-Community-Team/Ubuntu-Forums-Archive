---
title: "usertable broken or something?"
date: 2010-09-28
forum: General Help
---

### Post by thegreatbeste on 2010-09-28
Could someone explain that to me?
I tried to install the new teamspeak server.
As i dont run the server as root i use the user teamspeak.
But there seems to be something broken with permissions.
I said *$chown -R teamspeak teamspeak3-server_linux-x86* but all i get ist this:

```
root@h1318331:/home/teamspeak/teamspeak3-server_linux-x86# ls -la
total 7516
drwxr-xr-x 7 teamspeak httpd        4096 2010-09-09 09:52 .
drwxr-xr-x 6 teamspeak teamspeak    4096 2010-09-28 23:41 ..
-rw-r--r-- 1 teamspeak httpd       24489 2010-09-09 09:52 CHANGELOG
drwxr-xr-x 2 teamspeak httpd        4096 2010-09-09 09:52 doc
drwx------ 3 teamspeak root         4096 2010-02-27 10:34 files
-rwxr-xr-x 1 teamspeak httpd      208134 2010-09-09 09:52 libts3db_mysql.so
-rwxr-xr-x 1 teamspeak httpd      840866 2010-09-09 09:52 libts3db_sqlite3.so
-rw-r--r-- 1 teamspeak httpd       24099 2010-09-09 09:52 LICENSE
drwx------ 2 teamspeak root         4096 2010-02-27 10:37 logs
-rw-r--r-- 1 teamspeak root           10 2010-02-27 10:34 query_ip_whitelist.txt
drwxr-xr-x 2 teamspeak httpd        4096 2010-09-09 09:52 serverquerydocs
drwxr-xr-x 4 teamspeak httpd        4096 2010-09-09 09:52 sql
-rwxr-xr-x 1 teamspeak httpd     6311052 2010-09-09 09:52 ts3server_linux_x86
-rwxr-xr-x 1 teamspeak httpd         328 2010-09-09 09:52 ts3server_minimal_runscript.sh
-rw-r--r-- 1 teamspeak teamspeak       6 2010-02-27 10:37 ts3server.pid
-rw-r--r-- 1 teamspeak root       212992 2010-02-27 11:03 ts3server.sqlitedb
-rwxr-xr-x 1 teamspeak httpd        2735 2010-09-09 09:52 ts3server_startscript.sh
root@h1318331:/home/teamspeak/teamspeak3-server_linux-x86# su teamspeak
teamspeak@h1318331:~$ cd teamspeak3-server_linux-x86
teamspeak@h1318331:~/teamspeak3-server_linux-x86$ ls -la
total 20
drwxr-xr-x 5 teamspeak      1000 4096 Sep 28 21:39 .
drwx------ 5 teamspeak teamspeak 4096 Sep 28 21:38 ..
drwxr-xr-x 2      1000      1000 4096 Jun  2 06:20 doc
drwxr-xr-x 2      1000      1000 4096 Jun  2 06:21 serverquerydocs
drwxr-xr-x 4      1000      1000 4096 Jun  2 06:21 sql
teamspeak@h1318331:~/teamspeak3-server_linux-x86$ exit
logout
root@h1318331:/home/teamspeak/teamspeak3-server_linux-x86# ls -la
total 7516
drwxr-xr-x 7 teamspeak httpd        4096 2010-09-09 09:52 .
drwxr-xr-x 6 teamspeak teamspeak    4096 2010-09-28 23:41 ..
-rw-r--r-- 1 teamspeak httpd       24489 2010-09-09 09:52 CHANGELOG
drwxr-xr-x 2 teamspeak httpd        4096 2010-09-09 09:52 doc
drwx------ 3 teamspeak root         4096 2010-02-27 10:34 files
-rwxr-xr-x 1 teamspeak httpd      208134 2010-09-09 09:52 libts3db_mysql.so
-rwxr-xr-x 1 teamspeak httpd      840866 2010-09-09 09:52 libts3db_sqlite3.so
-rw-r--r-- 1 teamspeak httpd       24099 2010-09-09 09:52 LICENSE
drwx------ 2 teamspeak root         4096 2010-02-27 10:37 logs
-rw-r--r-- 1 teamspeak root           10 2010-02-27 10:34 query_ip_whitelist.txt
drwxr-xr-x 2 teamspeak httpd        4096 2010-09-09 09:52 serverquerydocs
drwxr-xr-x 4 teamspeak httpd        4096 2010-09-09 09:52 sql
-rwxr-xr-x 1 teamspeak httpd     6311052 2010-09-09 09:52 ts3server_linux_x86
-rwxr-xr-x 1 teamspeak httpd         328 2010-09-09 09:52 ts3server_minimal_runscript.sh
-rw-r--r-- 1 teamspeak teamspeak       6 2010-02-27 10:37 ts3server.pid
-rw-r--r-- 1 teamspeak root       212992 2010-02-27 11:03 ts3server.sqlitedb
-rwxr-xr-x 1 teamspeak httpd        2735 2010-09-09 09:52 ts3server_startscript.sh
root@h1318331:/home/teamspeak/teamspeak3-server_linux-x86#

```

Any ideas?

---

