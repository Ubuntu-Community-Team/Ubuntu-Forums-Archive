---
title: "Install LTIB in Ubuntu10.04    MD5 ERROR"
date: 2010-09-23
forum: General Help
---

### Post by lhjoanna on 2010-09-23
I install the ltib in Ubuntu 10.04,first i met the rpm-build problem.I searched and found rpmbuild has already installed ,then  i add '#' before  the line   rpm-build  0     in ltib.  After this ,i tried   ./ltib   again,but  here comes the   md5sum match problem. I don't know how to solve this .  Anyone  met the same problem?or know how to solve this?  Thanks a lot !!!

Here is my  host_config.log
> 
Processing platform: host support
===================================

Processing: rpm-fs
====================
Build path taken because: no prebuilt rpm, 
Testing network connectivity for gpp
OK GPP: is available
Try rpm-4.0.4.tar.gz.md5 from the GPP
2010-09-23 12:53:26 URL:[http://bitshrine.org/gpp//rpm-4.0.4.tar.gz.md5](http://bitshrine.org/gpp//rpm-4.0.4.tar.gz.md5) [50/50] -> "rpm-4.0.4.tar.gz.md5" [1]
Try rpm-4.0.4.tar.gz from the GPP
ERROR: md5sum mismatch, re-naming /tmp/rpm-root/rpm-4.0.4.tar.gz to /tmp/rpm-root/rpm-4.0.4.tar.gz.bad, please re-try
Can't get: rpm-4.0.4.tar.gz at ./ltib line 802.
Died at ./ltib line 2471.
traceback:
 main::check_rpm_setup:2471
  main::host_checks:1456
   main:548


Started: Thu Sep 23 12:53:22 2010
Ended:   Thu Sep 23 12:56:14 2010
Elapsed: 172 seconds

Use of uninitialized value in concatenation (.) or string at ./ltib line 2791.
Use of uninitialized value in concatenation (.) or string at ./ltib line 2791.
VERSION          : 10.1.1
CVS_VERSION      : $Revision: 1.71 $ (Savannah)
PLATFORM         : host
GNUTARCH         : i686
TOOLCHAIN        : 
TOOLCHAIN_CFLAGS : 

These packages failed to build:
rpm-fs 

Build Failed


Thank you very much!!

---

