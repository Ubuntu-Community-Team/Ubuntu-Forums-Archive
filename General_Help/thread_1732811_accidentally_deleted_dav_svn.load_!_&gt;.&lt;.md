---
title: "accidentally deleted dav_svn.load ! &gt;.&lt;"
date: 2011-04-18
forum: General Help
---

### Post by tyrick on 2011-04-18
As the title suggests, I accidentally deleted the following files from "/etc/apache2/mods-available/dav_svn.load" :

(I had some subversion issues and just wanted to completely reinstall it, but little did I know that these files were essential for apache to do basic things..) 

dav_svn.conf
dav_svn.load
dev_svn.config

Anyway for me to get them back without completely reinstalling? Thanks >.<

-Tyrick

---

### Post by WorMzy on 2011-04-18
You could reinstall the libapache2-svn package to get back the first two files, although any changes you've made to any other files provided by that package may be lost.

No idea about the last one, it's not included in any package in the repos.

```
sudo apt-get install --reinstall libapache2-svn
```

---

### Post by tyrick on 2011-04-18
Hmm... This is what I got when I tried that method

> britt@web-server:/etc/apache2/mods-available$ sudo apt-get install --reinstall libapache2-svn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libapache2-svn (1.6.12dfsg-1ubuntu1) ...
ERROR: /etc/apache2/mods-enabled/dav_svn.load is a dangling symlink!
ERROR: Module dav_svn does not exist!
dpkg: error processing libapache2-svn (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 libapache2-svn
E: Sub-process /usr/bin/dpkg returned an error code (1)


>.<

---

### Post by WorMzy on 2011-04-18
Run

```
sudo rm /etc/apache2/mods-enabled/dav_svn.load
```

then try again.

---

### Post by tyrick on 2011-04-18
Still had problems =/

> britt@web-server:/etc/apache2/mods-available$ sudo rm /etc/apache2/mods-enabled/dav_svn.load
[sudo] password for britt: 
britt@web-server:/etc/apache2/mods-available$ sudo apt-get install --reinstall libapache2-svn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up libapache2-svn (1.6.12dfsg-1ubuntu1) ...
ERROR: Module dav_svn does not exist!
dpkg: error processing libapache2-svn (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 libapache2-svn
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by WorMzy on 2011-04-18
How annoying. You may have to remove the page before it'll let you reinstall it. Unfortunately, I get the feeling that you won't be able to remove it, because it's no longer installed properly. Try it anyway:

```
sudo apt-get remove libapache2-svn
```
followed by (assuming that works)
```
sudo apt-get install libapache2-svn
```

---

### Post by tyrick on 2011-04-18
Ya, not looking good. =/

> britt@web-server:/etc/apache2/mods-available$ sudo apt-get remove libapache2-svn[sudo] password for britt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libapache2-svn
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 381kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 57588 files and directories currently installed.)
Removing libapache2-svn ...
britt@web-server:/etc/apache2/mods-available$ sudo apt-get install libapache2-svn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  db4.8-util
The following NEW packages will be installed:
  libapache2-svn
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/165kB of archives.
After this operation, 381kB of additional disk space will be used.
Selecting previously deselected package libapache2-svn.
(Reading database ... 57576 files and directories currently installed.)
Unpacking libapache2-svn (from .../libapache2-svn_1.6.12dfsg-1ubuntu1_i386.deb) ...
Setting up libapache2-svn (1.6.12dfsg-1ubuntu1) ...
ERROR: Module dav_svn does not exist!
dpkg: error processing libapache2-svn (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 libapache2-svn
E: Sub-process /usr/bin/dpkg returned an error code (1)
britt@web-server:/etc/apache2/mods-available$ 


---

### Post by WorMzy on 2011-04-18
One final suggestion from me then, try purging it.

```
sudo apt-get purge libapache2-svn
```

---

### Post by tyrick on 2011-04-18
haha.. Success! Thanks a lot! Appreciate your patience!

---

### Post by WorMzy on 2011-04-18
Haha, no problem. They do like to make this difficult some times. :)

Glad you got it sorted.

---

