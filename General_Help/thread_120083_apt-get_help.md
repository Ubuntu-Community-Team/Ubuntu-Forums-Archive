---
title: "apt-get help"
date: 2006-01-20
forum: General Help
---

### Post by njzillest on 2006-01-20
I have been treing to install firestarter through apt-get. Every time i try it doesnt work, this is the problem. Any suggestions?

thanx alot
-Adel


njzillest@belkin:~$ sudo apt-get install firestarter
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  firestarter
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
njzillest@belkin:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

---

### Post by darth_vector on 2006-01-20
are you using synaptic at the same time? you cant have synaptic open and be using aptitude at the same time.

if not, do this```
sudo rm -rf /var/lib/apt/lists/lock
sudo apt-get update
sudo apt-get install firestarter
```

---

