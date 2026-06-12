---
title: "Can't remove postgresql?"
date: 2010-02-24
forum: General Help
---

### Post by ubuntüser on 2010-02-24
This is what I get:
I think its partially removed or something.

```
server@A-srvr:~$ sudo apt-get remove --purge postgresql
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  postgresql-8.4 postgresql-common postgresql-client-8.4 postgresql-client-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  postgresql*
0 upgraded, 0 newly installed, 1 to remove and 96 not upgraded.
2 not fully installed or removed.
After this operation, 45.1kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 137159 files and directories currently installed.)
Removing postgresql ...
Setting up postgresql-8.4 (8.4.2-0ubuntu9.10) ...
 * Starting PostgreSQL 8.4 database server
 * Error: /var/lib/postgresql/8.4/main is not accessible or does not exist
   ...fail!
invoke-rc.d: initscript postgresql-8.4, action "start" failed.
dpkg: error processing postgresql-8.4 (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 postgresql-8.4
E: Sub-process /usr/bin/dpkg returned an error code (1)

server@A-srvr:~$ dpkg -l | grep postgre
rF  postgresql-8.4                       8.4.2-0ubuntu9.10                          object-relational SQL database, version 8.4
ii  postgresql-client-8.4                8.4.2-0ubuntu9.10                          front-end programs for PostgreSQL 8.4
ii  postgresql-client-common             101                                        manager for multiple PostgreSQL client versi
ii  postgresql-common                    101                                        PostgreSQL database-cluster manager

server@A-srvr:/var/lib$ sudo dpkg -r postgresql-8.4
(Reading database ... 137155 files and directories currently installed.)
Removing postgresql-8.4 ...
 * Stopping PostgreSQL 8.4 database server
 * Error: /var/lib/postgresql/8.4/main is not accessible or does not exist
   ...fail!
invoke-rc.d: initscript postgresql-8.4, action "stop" failed.
dpkg: error processing postgresql-8.4 (--remove):
 subprocess installed pre-removal script returned error exit status 1
 * Starting PostgreSQL 8.4 database server
 * Error: /var/lib/postgresql/8.4/main is not accessible or does not exist
   ...fail!
invoke-rc.d: initscript postgresql-8.4, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 postgresql-8.4

```

How do I remove pgsql completely?

EDIT: Fixed it myself:

Do this: sudo nano /var/lib/dpkg/info/postgresql-8.4.prerm
After first like (which is #/bin/sh -e)
add exit 0

Then:

```
server@A-srvr:/var/lib$ sudo dpkg -r postgresql-8.4
(Reading database ... 137155 files and directories currently installed.)
Removing postgresql-8.4 ...
Processing triggers for sreadahead ...

```

it worked!

---

### Post by clegends on 2010-08-31
Thanks heaps. Worked for me also.

---

### Post by egbutter on 2011-06-10
Thanks for this pointer!  I did not understand where these uninstall files lived.    Are the postremove files @ //var/lib/dpkg/info/postgresql-* supposed to be there, or are they supposed to be removed too?    Cheers,

---

### Post by maya123ca on 2011-11-10
Thanks for this. It enabled me to remove zramswap-enabler, which gave me the same error message when I first tried to uninstall it.

---

### Post by sl410 on 2012-06-07
thanks .. this help me to remove the zramswap-enabler too! ubuntu r0x!! \m/     :guitar:
im currently using ubuntu 12.04 , and the zramswap-enabler messed up after doing some upgrade..  yeah ! found the solution here!

---

