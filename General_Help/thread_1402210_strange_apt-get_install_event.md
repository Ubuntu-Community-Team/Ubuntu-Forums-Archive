---
title: "strange apt-get install event"
date: 2010-02-08
forum: General Help
---

### Post by shahansudu on 2010-02-08
Hi,
   I was trying to install packages in the my Ubuntu 9.04 desktop version (64 bit) and I keep seeing this strange event where apt-get try to setup snort-mysql and in doing so it try to stop snort and mysql and then start. My installation is not related to either snort nor mysql. Can someone explain this to me, thank you in advance. Following is what I keep seeing

```

$ sudo apt-get install python2.6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python2.6-dev is already the newest version.
python2.6-dev set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up snort-mysql (2.7.0-22ubuntu1) ...
 * Stopping Network Intrusion Detection System  snort                                                                                                                            * No running snort instance found
 * Starting Network Intrusion Detection System  snort                                                                                                                            * /etc/snort/db-pending-config file found
 * Snort will not start as its database is not yet configured.
 * Please configure the database as described in
 * /usr/share/doc/snort-{pgsql,mysql}/README-database.Debian
 * and remove /etc/snort/db-pending-config
invoke-rc.d: initscript snort, action "start" failed.
dpkg: error processing snort-mysql (--configure):
 subprocess post-installation script returned error exit status 6
Errors were encountered while processing:
 snort-mysql
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by shahansudu on 2010-02-08
so interestingly removing snort-mysql and snort have solved this problem. I'm assuming this was due to a incorrectly installed or incomplete install of package relating to the snort or snort-mysql. 

Does anyone know where I can look for such bad installs in apt (not very familiar with how apt works). If any one can direct me to where I can get more info on this or give me some insight on whether apt-get stores these info somewhere and whether it does any retries that is helpful.

---

