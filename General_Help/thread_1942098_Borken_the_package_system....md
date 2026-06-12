---
title: "Borken the package system..."
date: 2012-03-16
forum: General Help
---

### Post by doomtrader on 2012-03-16
So I'm new to Ubuntu.... as you can probably guess... and somehow I have managed to break the package system.  This is the error I am getting:

> The following packages have unmet dependencies:

libc6: Depends: libc-bin (= 2.13-20ubuntu5) but it is not installed
libc6-dev: Depends: libc6 (= 2.13-20ubuntu5.1) but 2.13-20ubuntu5 is installed
           Depends: libc-dev-bin (= 2.13-20ubuntu5.1) but 2.13-20ubuntu5.1 is installedIt recommends running the following command

sudo apt-get install -f

But the result of this does not help, and I end up with the following:

> 
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
1 upgraded, 1 newly installed, 0 to remove and 372 not upgraded.
2 not fully installed or removed.
Need to get 0 B/5,143 kB of archives.
After this operation, 3,432 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Can't exec "locale": No such file or directory at /usr/share/perl5/Debconf/Encoding.pm line 16.
Use of uninitialized value $Debconf::Encoding::charmap in scalar chomp at /usr/share/perl5/Debconf/Encoding.pm line 17.
Preconfiguring packages ...
dpkg: warning: 'ldconfig' not found in PATH or not executable.
dpkg: error: 1 expected program not found in PATH or not executable.
Note: root's PATH should usually contain /usr/local/sbin, /usr/sbin and /sbin.
E: Sub-process /usr/bin/dpkg returned an error code (2)Can any one please help?

---

### Post by cortman on 2012-03-16
Instructions given on the third and last posts of [this thread]("http://ubuntuforums.org/showthread.php?t=1266104") should help you resolve the issue.

---

### Post by jeremymiles on 2012-03-17
Hi, this didn't help me. 

The instructions say:

aptitude download libc6

It says:
jeremy@ubuntu:/etc$ aptitude download libc6
The program 'aptitude' can be found in the following packages:
 * aptitude
 * aptitude-gtk
Try: sudo apt-get install <selected package>

So I try apt-get instead:
jeremy@ubuntu:/etc$ sudo apt-get -f install libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.13-20ubuntu5.1)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


And we're back where we started.  :(

---

### Post by RobinJ on 2012-03-18
Deleted

---

### Post by cortman on 2012-03-18
> **jeremymiles said:**
> Hi, this didn't help me. 

The instructions say:

aptitude download libc6

It says:
jeremy@ubuntu:/etc$ aptitude download libc6
The program 'aptitude' can be found in the following packages:
 * aptitude
 * aptitude-gtk
Try: sudo apt-get install <selected package>

So I try apt-get instead:
jeremy@ubuntu:/etc$ sudo apt-get -f install libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libc6 : Depends: libc-bin (= 2.13-20ubuntu5.1)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


And we're back where we started.  :(

Have you tried

```
sudo apt-get install -f
```

by itself? (No package names)

---

