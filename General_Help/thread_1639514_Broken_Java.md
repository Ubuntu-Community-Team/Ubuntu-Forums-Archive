---
title: "Broken Java"
date: 2010-12-06
forum: General Help
---

### Post by yonthan on 2010-12-06
Now reading around I can see where I went wrong. When installing Java through terminal, when it asked me to accept, I couldn't work out how to select ok and eventually I just quit Terminal and now my Java install is broken and Im struggling to remove it.

I may have made a series of errors, once I exited Terminal, I tried to open synapic, and I got an error saying that the it was locked. So I manually removed the lock and now I cannot uninstall Java.

I tried sudo apt-get -f install and got this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  python-sip
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  sun-java6-jre
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
(Reading database ... 
dpkg: warning: files list file for package `sun-java6-jre' missing, assuming package has no files currently installed.
(Reading database ... 159436 files and directories currently installed.)
Removing sun-java6-jre ...
Setting up man-db (2.5.7-4) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 man-db
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by lykeion on 2010-12-07
According to [this]("https://wiki.edubuntu.org/DebuggingInstallationIssues#DbDriver%20%22config%22%20is%20locked") page, you could try to determine the locking process and its PID with this command:```
fuser -v /var/cache/debconf/config.dat
```
And kill that process with:```
sudo kill -9 <PID>
```
Note: "Most often, this is only a transient situation and fuser will return nothing. Simply performing the update again should solve this issue."

Also: [How to accept the license agreement in terminal when installing sun-java6-jre]("http://ubuntuforums.org/showthread.php?t=1604200")

---

### Post by yonthan on 2010-12-07
Thank! :) That worked! Im reinstalling Java now

---

