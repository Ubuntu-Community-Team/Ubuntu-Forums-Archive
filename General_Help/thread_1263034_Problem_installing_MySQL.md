---
title: "Problem installing MySQL"
date: 2009-09-10
forum: General Help
---

### Post by Jmz360 on 2009-09-10
I had MySQL installed on my Ubuntu computer and it was working. Then I noticed that it had stopped automatically starting when I started my computer. I tried a few different things but couldn't fix it, MySQL just wouldn't start.

I decided to uninstall MySQL and then reinstall it. But when I try to reinstall it says do you want to continue so I press Y and enter and then it says:

```

(Reading database ... 109684 files and directories currently installed.)
Removing mysql-server-5.0 ...
 * Stopping MySQL database server mysqld                                            [ OK ] 
Purging configuration files for mysql-server-5.0 ...
Removing mysql-client-5.0 ...
Processing triggers for man-db ...
james@DevServer:~$ sudo apt-get --purge remove mysql-server-5.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mysql-server-5.0 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libnet-daemon-perl libhtml-template-perl libdbi-perl libdbd-mysql-perl libplrpc-perl
  mysql-server-core-5.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
james@DevServer:~$ y
bash: y: command not found
james@DevServer:~$ sudo apt-get install mysql-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  mysql-client-5.0 mysql-server-5.0
Suggested packages:
  mysql-doc-5.0 tinyca mailx
The following NEW packages will be installed
  mysql-client-5.0 mysql-server mysql-server-5.0
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/31.5MB of archives.
After this operation, 98.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
Selecting previously deselected package mysql-client-5.0.
(Reading database ... 107323 files and directories currently installed.)
Unpacking mysql-client-5.0 (from .../mysql-client-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb) ...
Selecting previously deselected package mysql-server-5.0.
Unpacking mysql-server-5.0 (from .../mysql-server-5.0_5.1.30really5.0.75-0ubuntu10.2_i386.deb) ...
Selecting previously deselected package mysql-server.
Unpacking mysql-server (from .../mysql-server_5.1.30really5.0.75-0ubuntu10.2_all.deb) ...
Processing triggers for man-db ...
Setting up mysql-client-5.0 (5.1.30really5.0.75-0ubuntu10.2) ...
Setting up mysql-server-5.0 (5.1.30really5.0.75-0ubuntu10.2) ...
 * Stopping MySQL database server mysqld                                            [ OK ] 
 * Reloading AppArmor profiles ...                                                  [ OK ] 
 * Starting MySQL database server mysqld                                            [fail] 
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.0; however:
  Package mysql-server-5.0 is not configured yet.
dpkg: error processing mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
               Errors were encountered while processing:
 mysql-server-5.0
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Does anybody know how I can fix this?

---

### Post by prem1er on 2009-09-10
```
sudo apt-get --purge remove mysql-server
```

Then reinstall.

---

### Post by Jmz360 on 2009-09-14
I got that sorted. I needed to change the IP for the bind address in my my.cnf

---

