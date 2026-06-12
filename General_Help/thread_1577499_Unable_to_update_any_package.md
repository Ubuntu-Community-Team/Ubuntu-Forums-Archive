---
title: "Unable to update any package"
date: 2010-09-18
forum: General Help
---

### Post by ansariemail on 2010-09-18
I am unable to update any package due to some error in acroread:
------

Preconfiguring packages ...
(Reading database ... 318647 files and directories currently installed.)
Preparing to replace acroread 9.3.3-1lucid1 (using .../acroread_9.3.4-1lucid1_amd64.deb) ...
Unpacking replacement acroread ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
A package failed to install.  Trying to recover:
Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
---

If I try to remove acroread, here's what I get:

sudo apt-get remove acroread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libparted0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  acroread
0 upgraded, 0 newly installed, 1 to remove and 54 not upgraded.
1 not fully installed or removed.
After this operation, 152MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: error processing acroread (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 acroread
E: Sub-process /usr/bin/dpkg returned an error code (1)

---
sudo apt-get autoremove doesn't help either

---

If I try to update any other package, the progress stops with the error at the top of this message.

---

### Post by andrewthomas on 2010-09-19
[B]Package is in a very bad inconsistent state - you should
reinstall it before attempting a removal.[/B]
 
 
Did you try to reinstall the package as the error message stated?

---

### Post by ansariemail on 2010-09-19
I tried installing, removing, updating... nothing works. All end with some error:

sudo apt-get install acroread
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libldap2
The following packages will be upgraded:
  acroread
1 upgraded, 0 newly installed, 0 to remove and 54 not upgraded.
1 not fully installed or removed.
Need to get 0B/63.4MB of archives.
After this operation, 4,096B of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package acroread.
(Reading database ... 318643 files and directories currently installed.)
Preparing to replace acroread 9.3.3-1lucid1 (using .../acroread_9.3.4-1lucid1_amd64.deb) ...
Unpacking replacement acroread ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

---

### Post by andrewthomas on 2010-09-19
try 
```
 
sudo apt-get install acroread --reinstall

```
 
or try```
 
sudo aptitude reinstall acroread
``` 
post any error message

---

### Post by ansariemail on 2010-09-20
Unfortunately, neither of the commands succeeded.

$sudo apt-get install acroread --reinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  libldap2
The following packages will be upgraded:
  acroread
1 upgraded, 0 newly installed, 0 to remove and 54 not upgraded.
1 not fully installed or removed.
Need to get 63.4MB of archives.
After this operation, 4,096B of additional disk space will be used.
Get:1 [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner acroread 9.3.4-1lucid1 [63.4MB]
Fetched 63.4MB in 2min 30s (420kB/s)                                           
Preconfiguring packages ...
(Reading database ... 318643 files and directories currently installed.)
Preparing to replace acroread 9.3.3-1lucid1 (using .../acroread_9.3.4-1lucid1_amd64.deb) ...
Unpacking replacement acroread ...
dpkg: ../../src/archives.c:763: tarobject: Assertion `r == stab.st_size' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly



$ sudo aptitude reinstall acroread
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
The following packages will be REINSTALLED:
  acroread 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 54 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the acroread package. This might mean you need to manually fix this package.
Writing extended state information... Done
E: I wasn't able to locate file for the acroread package. This might mean you need to manually fix this package.
E: Internal error: couldn't generate list of packages to download

---

