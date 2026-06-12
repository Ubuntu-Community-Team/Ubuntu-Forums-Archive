---
title: "proplem - The Ubuntu desktop system Broken Package How i can fix it ?"
date: 2006-01-26
forum: General Help
---

### Post by sharif_aly on 2006-01-26
The Ubuntu desktop system

E: /var/cache/apt/archives/slocate_2.7-4_i386.deb: subprocess pre-installation script returned error exit status 2

---

### Post by sharif_aly on 2006-01-26
sudo apt-get install -f ubuntu-desktop
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
user@group:~$ sudo apt-get install -f ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
ubuntu-desktop is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  ubuntu-desktop: Depends: slocate but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
user@group:~$ sudo apt-get install -f slocate
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  slocate
0 upgraded, 1 newly installed, 0 to remove and 44 not upgraded.
380 not fully installed or removed.
Need to get 0B/27.0kB of archives.
After unpacking 147kB of additional disk space will be used.

Preconfiguring packages ...
(Reading database ... 55931 files and directories currently installed.)
Unpacking slocate (from .../slocate_2.7-4_i386.deb) ...
Removing `diversion of /etc/cron.daily/find to /etc/cron.daily/find.notslocate by slocate'
dpkg-divert: rename involves overwriting `/etc/cron.daily/find' with
  different file `/etc/cron.daily/find.notslocate', not allowed
dpkg: error processing /var/cache/apt/archives/slocate_2.7-4_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/slocate_2.7-4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Adrian on 2006-01-26
I usually try Synaptic when I run into similar problems. Sometimes it works :)

---

### Post by snooptodd on 2006-01-26
Try this, it worked for me.

```
rm /etc/cron.daily/find
dpkg-divert --rename --remove /etc/cron.daily/find 
```

---

### Post by sharif_aly on 2006-01-26
snooptodd, thanks works fine :)
but when come " Permission denied" i use sudo
sudo rm /etc/cron.daily/find
sudo dpkg-divert --rename --remove /etc/cron.daily/find

---

### Post by sharif_aly on 2006-03-01
W: Couldn't stat source package list file: breezy/main Packages (/var/lib/apt/lists/_cdrom_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)

---

