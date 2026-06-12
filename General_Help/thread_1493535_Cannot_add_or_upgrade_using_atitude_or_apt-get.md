---
title: "Cannot add or upgrade using atitude or apt-get"
date: 2010-05-25
forum: General Help
---

### Post by c0mputerking on 2010-05-25
I am running Ubuntu 8.04 LTS Server edition and am having problems upgrading or adding new packages.  I have run aptitude update and upgrade and get the message below.  Have also tried running apt-get update, apt-get upgrade, apt-get -f install,  apt-get autoremove nothing is getting me past these errors see farther below.

The offending package is bacula which i have installed from source now! as the package apt-get is trying to install is to old anyways. 

Please someone help me with this as I have posted several times and never get any helpfull info. 

Get:84 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) hardy-updates/main texlive-base-bin 2007.dfsg.1-2ubuntu0.1 [2384kB]
Fetched 92.1MB in 41s (2213kB/s)                                                
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 108907 files and directories currently installed.)
Removing bacula-director-mysql ...
invoke-rc.d: unknown initscript, /etc/init.d/bacula-director not found.
dpkg: error processing bacula-director-mysql (--remove):
 subprocess pre-removal script returned error exit status 100
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 100
Errors were encountered while processing:
 bacula-director-mysql
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done

---

### Post by exodus_ on 2010-05-25
A quick [google search]("http://www.google.com/search?client=ubuntu&channel=fs&q=invoke-rc.d%3A+unknown+initscript%2C+%2Fetc%2Finit.d%2Fbacula-director+not+found.&ie=utf-8&oe=utf-8") brought me to [this post]("http://ubuntuforums.org/showthread.php?t=1420625") which might help solve this.

---

### Post by c0mputerking on 2010-05-26
Thanks a bunch that did it

---

