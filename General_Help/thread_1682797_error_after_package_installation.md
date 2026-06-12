---
title: "error after package installation"
date: 2011-02-06
forum: General Help
---

### Post by dpwilson on 2011-02-06
Need help with error message I receive after any package is installed or any update installed.  It seems that the packages are installed and I am guessing that the update is the same, however, I get this message everytime.  Any ideas?  The message slightly differs at the "processing triggers" part depending on the package I install.


[FONT="System"]installArchives() failed: Selecting previously deselected package gnome-schedule.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 197928 files and directories currently installed.)
Unpacking gnome-schedule (from .../gnome-schedule_2.1.1-3_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Setting up ipheth-dkms (1.0+git20100207-1ubuntu1~ppa2) ...
Removing old ipheth-1.0+git20100207 DKMS files...

------------------------------
Deleting module version: 1.0+git20100207
completely from the DKMS tree.
------------------------------
Done.
Loading new ipheth-1.0+git20100207 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-25-generic
Building initial module for 2.6.35-25-generic

Error! Bad return status for module build on kernel: 2.6.35-25-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/ipheth/1.0+git20100207/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/ipheth-dkms.0.crash'
dpkg: error processing ipheth-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up gnome-schedule (2.1.1-3) ...
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 ipheth-dkms
Setting up ipheth-dkms (1.0+git20100207-1ubuntu1~ppa2) ...
Removing old ipheth-1.0+git20100207 DKMS files...

------------------------------
Deleting module version: 1.0+git20100207
completely from the DKMS tree.
------------------------------
Done.
Loading new ipheth-1.0+git20100207 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-25-generic
Building initial module for 2.6.35-25-generic

Error! Bad return status for module build on kernel: 2.6.35-25-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/ipheth/1.0+git20100207/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/ipheth-dkms.0.crash'
dpkg: error processing ipheth-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10[/FONT]

---

### Post by dino99 on 2011-02-06
clean the sources:

sudo rm /var/cache/apt/archives/*

sudo dpkg --configure -a

then update, upgrade

---

### Post by dpwilson on 2011-02-06
this is what I get after dpkg

[FONT="System"]wilson@wilson-desktop:~$ sudo dpkg --configure -a
Setting up ipheth-dkms (1.0+git20100207-1ubuntu1~ppa2) ...
Removing old ipheth-1.0+git20100207 DKMS files...

------------------------------
Deleting module version: 1.0+git20100207
completely from the DKMS tree.
------------------------------
Done.
Loading new ipheth-1.0+git20100207 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-25-generic
Building initial module for 2.6.35-25-generic

Error! Bad return status for module build on kernel: 2.6.35-25-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/ipheth/1.0+git20100207/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/ipheth-dkms.0.crash'
dpkg: error processing ipheth-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 ipheth-dkms[/FONT]

---

### Post by greg_lw on 2011-02-10
> **dpwilson said:**
> this is what I get after dpkg

Similar problem here, trying to install virtualbox-ose on Ubuntu Server 10.10 / 2.6.35-25-generic. 

```


------------------------------
Deleting module version: 3.2.8
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-ose-3.2.8 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-25-generic
Building initial module for 2.6.35-25-generic

Error! Bad return status for module build on kernel: 2.6.35-25-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/virtualbox-ose/3.2.8/build/ for more information.
dpkg: error processing virtualbox-ose-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 virtualbox-ose-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by dpwilson on 2011-02-18
I am still having the same problem installing any packages or doing updates.  I did the above mentioned and posted the results.  As I said before, it appears that packages and updates are being installed, I just keeping getting an error message afterwards.  Also, I think it may be related to this

```
dpkg: error processing ipheth-dkms (--configure):
```

Any help?

---

### Post by dpwilson on 2011-02-18
I think I solved it.  I removed the ipheth-dkms package and did an update and no error.   Will close this as solved.

---

