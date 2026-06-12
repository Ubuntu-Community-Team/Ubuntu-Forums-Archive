---
title: "Problem with installing/upgrading/uninstalling packages."
date: 2009-10-10
forum: General Help
---

### Post by Bobbino on 2009-10-10
Whenever I try to install, or remove, or reinstall or do anything package related really I get random, and annoying errors I can't fix. Wondering if anyone can shed some light or offer a possible solution?

```
bobbin@mini-bobbin:~$ sudo apt-get remove apache2
[sudo] password for bobbin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsoup2.2-8 gcj-4.2-base
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  apache2
0 upgraded, 0 newly installed, 1 to remove and 158 not upgraded.
15 not fully installed or removed.
Need to get 0B/27.4MB of archives.
After this operation, 102kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 159973 files and directories currently installed.)
Preparing to replace mysql-server-5.0 5.0.51a-3ubuntu5.1 (using .../mysql-server-5.0_5.0.51a-3ubuntu5.1_lpia.deb) ...
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.0.51a-3ubuntu5.1_lpia.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.0.51a-3ubuntu5.1_lpia.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

If i try to remove mysql_server-5.0 I get this...

```
bobbin@mini-bobbin:~$ sudo apt-get remove apache2
[sudo] password for bobbin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsoup2.2-8 gcj-4.2-base
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  apache2
0 upgraded, 0 newly installed, 1 to remove and 158 not upgraded.
15 not fully installed or removed.
Need to get 0B/27.4MB of archives.
After this operation, 102kB disk space will be freed.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
(Reading database ... 159973 files and directories currently installed.)
Preparing to replace mysql-server-5.0 5.0.51a-3ubuntu5.1 (using .../mysql-server-5.0_5.0.51a-3ubuntu5.1_lpia.deb) ...
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.0.51a-3ubuntu5.1_lpia.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.0.51a-3ubuntu5.1_lpia.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

so I did what it said, and tried to reinstall....

```
bobbin@mini-bobbin:~$ sudo apt-get install mysql-server-5.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsoup2.2-8 gcj-4.2-base
Use 'apt-get autoremove' to remove them.
Suggested packages:
  mysql-doc-5.0 tinyca
Recommended packages:
  apparmor libhtml-template-perl mailx
The following packages will be upgraded:
  mysql-server-5.0
1 upgraded, 0 newly installed, 0 to remove and 157 not upgraded.
15 not fully installed or removed.
Need to get 27.4MB of archives.
After this operation, 4096B of additional disk space will be used.
Get: 1 http://dell-mini.archive.canonical.com hardy-dell-mini/public mysql-server-5.0 5.0.51a-3ubuntu5.4 [27.4MB]
Fetched 27.4MB in 6min19s (72.0kB/s)                                                                                                                        
Preconfiguring packages ...
Selecting previously deselected package mysql-server-5.0.
(Reading database ... 159973 files and directories currently installed.)
Preparing to replace mysql-server-5.0 5.0.51a-3ubuntu5.1 (using .../mysql-server-5.0_5.0.51a-3ubuntu5.4_lpia.deb) ...
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/mysql-server-5.0_5.0.51a-3ubuntu5.4_lpia.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "stop" failed.
/etc/lsb-base-logging.sh: line 84: INITOUTPUT: unbound variable
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/mysql-server-5.0_5.0.51a-3ubuntu5.4_lpia.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And I got a crash report too!

```
Sorry, the package "mysql-server-5.0 5.0.51a-3ubuntu5.4" failed to install or upgrade.
```

Running ubuntu 8.04 on a Dell mini 12.

Thanks

Bobbin.

---

### Post by Bobbino on 2009-10-11
Bump...

---

### Post by sidlinger on 2009-10-21
I am experiencing exactly the same think on my Dell Mini 9.

---

### Post by slochewie on 2009-12-17
this is still a problem... Should Ubuntu 8.04 LTI not LTS for Long Term Ignore

---

