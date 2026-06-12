---
title: "Broadcom 10.10 install problem"
date: 2010-10-19
forum: General Help
---

### Post by TheNessus on 2010-10-19
Hi all,

I am trying to install  Broadcom 802.11 Linux STA wireless driver on my 10.10 64 bit fresh install. Have no internet connectivity obviously. I have a pendrive as a live USB. I do not know how to make a pendrive be a cd repository so I install it and dependencies each at a time. This worked perfectly on a 10.4 32 bit fresh install. 

However, I get this

An unhandlable error occurred
There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.



And with terminal, this:

jeff@jeff-Inspiron-N3010:~$ cd 
jeff@jeff-Inspiron-N3010:~$ cd Desktop 
jeff@jeff-Inspiron-N3010:~/Desktop$ sudo dpkg --install  bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb  
[sudo] password for jeff:  
(Reading database ... 117839 files and directories currently installed.) 
Preparing to replace bcmwl-kernel-source 5.60.48.36+bdcom-0ubuntu5 (using bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_amd64.deb) ... 
Removing all DKMS Modules 
Done. 
Unpacking replacement bcmwl-kernel-source ... 
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu5) ... 
Loading new bcmwl-5.60.48.36+bdcom DKMS files... 
First Installation: checking all kernels... 
Building only for 2.6.35-22-generic 
Building for architecture x86_64 
Building initial module for 2.6.35-22-generic 
/usr/sbin/dkms: line 35: patch: command not found 
 
Error! Application of patch 0001-MODULE_LICENSE.patch failed. 
Check /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information. 
Traceback (most recent call last): 
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module> 
    report.write(open(apport.fileutils.make_report_path(report), 'w')) 
IOError: [Errno 2] No such file or directory: '/var/crash/bcmwl-kernel-source.0.crash' 
dpkg: error processing bcmwl-kernel-source (--install): 
 subprocess installed post-installation script returned error exit status 6 
Errors were encountered while processing: 
 bcmwl-kernel-source 

so help would be awesomeness. :)

---

### Post by cloudshao on 2010-10-21
The output says:
```
/usr/sbin/dkms: line 35: patch: command not found
```

You need to install patch. On the Ubuntu CD, it can be found in /pool/main/p/patch. Also, I *think* I remember dkms and fakeroot being dependencies as well.

---

