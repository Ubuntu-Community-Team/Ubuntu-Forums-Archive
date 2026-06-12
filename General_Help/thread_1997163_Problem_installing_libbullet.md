---
title: "Problem installing libbullet"
date: 2012-06-04
forum: General Help
---

### Post by unitedanarchy on 2012-06-04
(Reading database ... 293295 files and directories currently installed.)
Unpacking libbullet0 (from .../libbullet0_2.77-1~getdeb2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libbullet0_2.77-1~getdeb2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libMiniCL.so.2.77', which is also in package libbullet1 2.77-0ppa1
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libbullet0_2.77-1~getdeb2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Press return to continue.

---

### Post by maverickaddicted on 2012-06-05
> **unitedanarchy said:**
> (Reading database ... 293295 files and directories currently installed.)
Unpacking libbullet0 (from .../libbullet0_2.77-1~getdeb2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libbullet0_2.77-1~getdeb2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libMiniCL.so.2.77', which is also in package libbullet1 2.77-0ppa1
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libbullet0_2.77-1~getdeb2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Press return to continue.

The error says -

```
No apport report written because MaxReports is reached already
```

Apport is a crash manager for Ubuntu. Apport generates all the crash files in /var/crash directory. I think going in there and deleting .crash file will help you to get rid of that message.

Also you can find more about Apport here -

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

---

### Post by unitedanarchy on 2012-06-05
valeskagrim@ValeskaGrim:~$ cd '/var/crash' 
valeskagrim@ValeskaGrim:/var/crash$ sudo '/var/crash/libbullet0.0.crash' 
[sudo] password for valeskagrim: 
sudo: /var/crash/libbullet0.0.crash: command not found
valeskagrim@ValeskaGrim:/var/crash$ sudo rm '/var/crash/libbullet0.0.crash' 
valeskagrim@ValeskaGrim:/var/crash$ cd
valeskagrim@ValeskaGrim:~$ sudo aptitude
(Reading database ... 295013 files and directories currently installed.)
Unpacking libbullet0 (from .../libbullet0_2.77-1~getdeb2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libbullet0_2.77-1~getdeb2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libMiniCL.so.2.77', which is also in package libbullet1 2.77-0ppa1
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libbullet0_2.77-1~getdeb2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Press return to continue.

---

### Post by maverickaddicted on 2012-06-06
> **unitedanarchy said:**
> valeskagrim@ValeskaGrim:~$ cd '/var/crash' 
valeskagrim@ValeskaGrim:/var/crash$ sudo '/var/crash/libbullet0.0.crash' 
[sudo] password for valeskagrim: 
sudo: /var/crash/libbullet0.0.crash: command not found
valeskagrim@ValeskaGrim:/var/crash$ sudo rm '/var/crash/libbullet0.0.crash' 
valeskagrim@ValeskaGrim:/var/crash$ cd
valeskagrim@ValeskaGrim:~$ sudo aptitude
(Reading database ... 295013 files and directories currently installed.)
Unpacking libbullet0 (from .../libbullet0_2.77-1~getdeb2_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/libbullet0_2.77-1~getdeb2_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/libMiniCL.so.2.77', which is also in package libbullet1 2.77-0ppa1
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libbullet0_2.77-1~getdeb2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Press return to continue.

Try disabling the apport report, it is explained in the wiki link which I have given to you.

---

