---
title: "Help to recover removed dependencies"
date: 2009-12-05
forum: General Help
---

### Post by pfwd.tech on 2009-12-05
Hi 
I foolishly did a 
 sudo apt-get autoremove --purge libsqlite* out of frustration on my home dev webserver.
Its removed a bunch of packages and dependencies that are required for other things.
Each time i do an update  I get the following:

```
:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  courier-authlib-userdb: Depends: courier-authlib (>= 0.60.1) but it is not installed
  courier-base: Depends: courier-authlib but it is not installed
E: Unmet dependencies. Try using -f.
:~$ sudo apt-get install -f  courier-authlib
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  liblaunchpad-integration1 libenchant1c2a cupsys-common libavahi-compat-libdnssd1 iso-codes
  libapr1 libffi4 libhunspell-1.1-0 libgtksourceview2.0-common libgtksourceview2.0-0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  courier-authdaemon
The following NEW packages will be installed
  courier-authlib
The following packages will be upgraded:
  courier-authdaemon
1 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
5 not fully installed or removed.
Need to get 0B/80.8kB of archives.
After this operation, 160kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing courier-authdaemon (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 courier-authdaemon
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Is there a way I can recover what I screwed up or am I looking at a complete re-installation?

---

### Post by pfwd.tech on 2009-12-05
I fixed this by doing:
```

# Back up the dpkg status
sudo cp /var/lib/dpkg/status /var/lib/dpkg/status-bkp
# Remove all occurrences of courier-* in dpkg/status
sudo nano /var/lib/dpkg/status
# CRTL + w to search for 'courier' and CTRL + k to cut the line
# Update the system
sudo apt-get update
# Upgrade the system
sudo apt-get upgrade
# Install courier-authdeamon
sudo apt-get install courier-authdaemon 

```Links to threads that helped me solve this:
[http://ubuntuforums.org/showthread.php?t=1339598](http://ubuntuforums.org/showthread.php?t=1339598)
[https://bugs.launchpad.net/ubuntu/+source/courier-authlib/+bug/64615](https://bugs.launchpad.net/ubuntu/+source/courier-authlib/+bug/64615)
Hope this helps someone in the future

---

