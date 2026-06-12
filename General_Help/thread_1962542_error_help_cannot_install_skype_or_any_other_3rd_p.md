---
title: "error help cannot install skype or any other 3rd party software"
date: 2012-04-21
forum: General Help
---

### Post by bigredyoshi on 2012-04-21
cannot install skype. the following error is displayed:

The following packages have unmet dependencies:

libc6: Depends: libc-bin (= 2.13-20ubuntu5) but it is not installed
libc6-dev: Depends: libc6 (= 2.13-20ubuntu5.1) but 2.13-20ubuntu5 is installed
           Depends: libc-dev-bin (= 2.13-20ubuntu5.1) but 2.13-20ubuntu5.1 is installed
libc6-i386: Depends: libc6 (= 2.13-20ubuntu5.1) but 2.13-20ubuntu5 is installed

---

### Post by kazztan0325 on 2012-04-21
Hi bigredyoshi,

Welcome to Ubuntu Forums!

> **bigredyoshi said:**
> cannot install skype. the following error is displayed:

The following packages have unmet dependencies:

libc6: Depends: libc-bin (= 2.13-20ubuntu5) but it is not installed
libc6-dev: Depends: libc6 (= 2.13-20ubuntu5.1) but 2.13-20ubuntu5 is installed
           Depends: libc-dev-bin (= 2.13-20ubuntu5.1) but 2.13-20ubuntu5.1 is installed
libc6-i386: Depends: libc6 (= 2.13-20ubuntu5.1) but 2.13-20ubuntu5 is installed

What version of Ubuntu are you using?

Have you read a following documentation?

"Ubuntu Documentation > Community Documentation > Skype"
[https://help.ubuntu.com/community/Skype]("https://help.ubuntu.com/community/Skype")

---

### Post by bigredyoshi on 2012-04-22
Version 11.10
I have not read the documentation however I attempted to install it from the ubuntu software center. Can't install playonlinux, gimp, ect. Without the following error:
The following packages have unmet dependencies:

libc6: Depends: libc-bin (= 2.13-20ubuntu5) but it is not installed
libc6-dev: Depends: libc6 (= 2.13-20ubuntu5.1) but 2.13-20ubuntu5 is installed
           Depends: libc-dev-bin (= 2.13-20ubuntu5.1) but 2.13-20ubuntu5.1 is installed
libc6-i386: Depends: libc6 (= 2.13-20ubuntu5.1) but 2.13-20ubuntu5 is installed

I hit "okay"

Items cannot be installed or removed until the package catalog is repaired. Do you want to repair it now?
"Repair"

package operation failed:
the installation or removal of a software has failed.
installArchives() failed: Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfiguring packages ...
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfiguring packages ...
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfiguring packages ...
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.

---

### Post by bigredyoshi on 2012-04-22
Another error is when i go into install my updates i get another error. 

The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

Details:
The following packages have unmet dependencies:

libc6: Depends: libc-bin (= 2.13-20ubuntu5) but it is not installed
libc6-dev: Depends: libc6 (= 2.13-20ubuntu5.1) but 2.13-20ubuntu5 is installed


           Depends: libc-dev-bin (= 2.13-20ubuntu5.1) but 2.13-20ubuntu5.1 is installed
libc6-i386: Depends: libc6 (= 2.13-20ubuntu5.1) but 2.13-20ubuntu5 is installed

So i go into terminal

Terminal:
apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by kazztan0325 on 2012-04-22
> **bigredyoshi said:**
> So i go into terminal

Terminal:
apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

You should type as below:

```
sudo apt-get install -f
```

What about the results?

---

### Post by bigredyoshi on 2012-04-22
These are the results from the following recommended command "sudo apt-get install -f"

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc-bin libc6
Suggested packages:
  glibc-doc
The following NEW packages will be installed:
  libc-bin
The following packages will be upgraded:
  libc6
1 upgraded, 1 newly installed, 0 to remove and 82 not upgraded.
3 not fully installed or removed.
Need to get 0 B/5,143 kB of archives.
After this operation, 3,432 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfiguring packages ...
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)

---

