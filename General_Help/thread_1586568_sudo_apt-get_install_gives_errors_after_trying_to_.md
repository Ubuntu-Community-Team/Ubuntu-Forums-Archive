---
title: "sudo apt-get install gives errors after trying to install bacula"
date: 2010-10-02
forum: General Help
---

### Post by fuzzylogic25 on 2010-10-02
I tried installing bacula and i really had no idea what i was doing and i believe it failed. I ran sudo apt-get install bacula. Anyway, I tried removing it using sudo apt-get remove bacula but now whenever i run sudo apt-get install for anything, the app will install but then show all these errors from bacula. how do i get rid of it?

---

### Post by stee1rat on 2010-10-02
I think you have to post the error message here..

---

### Post by fuzzylogic25 on 2010-10-02
here is what i get when i try to remove grsync:



==============================================================

john@cmp:~$ sudo apt-get remove grsync
[sudo] password for anthony: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  grsync
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 532kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 194769 files and directories currently installed.)
Removing grsync ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_AU.utf8.cache...
Processing triggers for python-support ...
Setting up bacula-director-mysql (5.0.1-1ubuntu1) ...
debconf: Unknown template field '_description', in stanza #9 of /var/lib/dpkg/info/bacula-director-mysql.templates

dbconfig-common: writing config to /etc/dbconfig-common/bacula-director-mysql.conf
Processing configuration...Ok.
 * Starting Bacula Director...                                                  02-Oct 23:41 bacula-dir: ERROR TERMINATION at lex.c:784
Config error: expected a string, got T_EOL: =
            : line 236, col 12 of file /etc/bacula/bacula-dir.conf
  dbname = ; DB Address = ""; dbuser = ""; dbpassword = ""

                                                                         [fail]
dpkg: error processing bacula-director-mysql (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bacula-server:
 bacula-server depends on bacula-director-mysql (>= 5.0.1-1ubuntu1) | bacula-director; however:
  Package bacula-director-mysql is not configured yet.
  Package bacula-director is not installed.
  Package bacula-director-mysql which provides bacula-director is not configured yet.
dpkg: error processing bacula-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 bacula-director-mysql
 bacula-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


==============================================================

---

### Post by vedavrata on 2010-10-05
The same problem:

```
Setting up bacula-director-mysql (5.0.1-1ubuntu1) ...
debconf: Unknown template field '_description', in stanza #9 of /var/lib/dpkg/info/bacula-director-mysql.templates
dbconfig-common: writing config to /etc/dbconfig-common/bacula-director-mysql.conf
Processing configuration...Ok.
 * Starting Bacula Director...
05-Oct 14:45 bacula-dir: ERROR TERMINATION at lex.c:784
Config error: expected a string, got T_EOL: =
            : line 236, col 12 of file /etc/bacula/bacula-dir.conf
  dbname = ; DB Address = ""; dbuser = ""; dbpassword = ""
                                                                            [fail]
dpkg: error processing bacula-director-mysql (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bacula-server:
 bacula-server depends on bacula-director-mysql (>= 5.0.1-1ubuntu1) | bacula-director; however:
  Package bacula-director-mysql is not configured yet.
  Package bacula-director is not installed.
  Package bacula-director-mysql which provides bacula-director is not configured yet.
dpkg: error processing bacula-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bacula:
 bacula depends on bacula-server; however:
  Package bacula-server is not configured yet.
dpkg: error processing bacula (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing:
 bacula-director-mysql
 bacula-server
 bacula
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Jack_Green on 2010-10-05
I think you have not install some packages.
You should find it in your terminal after trying to install bacula. 
There are some tips.

---

