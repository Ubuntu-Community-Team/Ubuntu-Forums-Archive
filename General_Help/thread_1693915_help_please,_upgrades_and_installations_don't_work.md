---
title: "help please, upgrades and installations don't work"
date: 2011-02-23
forum: General Help
---

### Post by quantumrider on 2011-02-23
for some reason upgrades or installations don't work anymore, I keep getting the same error message:

installArchives() failed: Setting up install-info (4.13a.dfsg.1-5ubuntu1) ... 
/etc/environment: line 2: MOZ_DISABLE_PANGO: command not found 
dpkg: error processing install-info (--configure): 
 subprocess installed post-installation script returned error exit status 127 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 install-info 
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ... 
/etc/environment: line 2: MOZ_DISABLE_PANGO: command not found 
dpkg: error processing install-info (--configure): 
 subprocess installed post-installation script returned error exit status 127 

helps please...

---

### Post by sanderd17 on 2011-02-23
What do you get when you type
```

sudo apt-get update

```

---

### Post by quantumrider on 2011-02-23
all seems ok except for skype...

W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by quantumrider on 2011-02-23
q@q:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  aptdaemon bind9-host dnsutils libbind9-60 libdns66 libisc60 libisccc60
  libisccfg60 liblwres60 python-aptdaemon python-aptdaemon-gtk
11 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/1,569kB of archives.
After this operation, 4,096B disk space will be freed.
Do you want to continue [Y/n]? y
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/etc/environment: line 2: MOZ_DISABLE_PANGO: command not found
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)
q@q:~$

---

### Post by wojox on 2011-02-23
Try this

```
gksudo gedit /etc/environment
```

Under your paths add this:

```
MOZ_DISABLE_PANGO = “1&#8243;
```

---

### Post by quantumrider on 2011-02-23
it's already in there... here is the content of the file:

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
MOZ_DISABLE_PANGO = "1"

---

### Post by wojox on 2011-02-23
> **quantumrider said:**
> it's already in there... here is the content of the file:

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
MOZ_DISABLE_PANGO = "1"

Try enabling, change it to "0".

---

### Post by quantumrider on 2011-02-23
tried it, same results 
q@q:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  aptdaemon bind9-host dnsutils libbind9-60 libdns66 libisc60 libisccc60
  libisccfg60 liblwres60 linux-headers-2.6.35-27
  linux-headers-2.6.35-27-generic linux-image-2.6.35-27-generic linux-libc-dev
  python-aptdaemon python-aptdaemon-gtk
15 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/47.5MB of archives.
After this operation, 45.1kB disk space will be freed.
Do you want to continue [Y/n]? y
Setting up install-info (4.13a.dfsg.1-5ubuntu1) ...
/etc/environment: line 2: MOZ_DISABLE_PANGO: command not found
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)
q@q:~$

---

### Post by plucky on 2011-02-23
> Errors were encountered while processing:
install-info

Try removing install-info ```
sudo apt-get remove install-info
```

Then clear out the apt archives with ```
sudo apt-get clean
``` so it will download a fresh copy of files to be installed.

Then run ```
sudo apt-get update
sudo apt-get upgrade
```

and see what happens.

Good Luck

---

### Post by quantumrider on 2011-02-23
yeah, that did it... thanks!!

---

### Post by amattheisen on 2011-03-09
I was having the same problems.  Here's how I caused the problem... While running the following command via ssh, I closed the terminal (oops).
 sudo aptitude safe-upgrade

To fix the problem I tried the following commands:
 sudo rm /var/cache/apt/*.bin
 sudo aptitude safe-upgrade
 sudo dpkg --configure -a
 sudo apt-get -f install

But they did not fix the problem.  Here is the output of the last command:
 Reading package lists... Done
 Building dependency tree       
 Reading state information... Done
 0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
 1 not fully installed or removed.
 After this operation, 0B of additional disk space will be used.
 Setting up xulrunner-1.9.2 (1.9.2.15+build1+nobinonly-0ubuntu0.10.04.1) ...
 /var/lib/dpkg/info/xulrunner-1.9.2.postinst: 5: /usr/bin/xulrunner-1.9.2: not found
 dpkg: error processing xulrunner-1.9.2 (--configure):
 subprocess installed post-installation script returned error exit status 127
 Errors were encountered while processing:
 xulrunner-1.9.2
 E: Sub-process /usr/bin/dpkg returned an error code (1)

So finally, I uninstalled the package "xulrunner-1.9.2" that aptitude was complaining about.
 sudo apt-get remove xulrunner-1.9.2
This also removed other packages that were dependent on xulrunner.  Finally I reinstalled xulrunner-1.9.2 and the dependent packages.
 sudo apt-get install couchdb-bin desktopcouch evolution-couchdb gnome-user-guide python-desktopcouch python-desktopcouch-records ubuntu-desktop ubuntu-docs xulrunner-1.9.2 yelp
Now I can update and install packages again.

---

