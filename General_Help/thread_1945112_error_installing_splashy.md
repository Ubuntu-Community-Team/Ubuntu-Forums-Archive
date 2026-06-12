---
title: "error installing splashy"
date: 2012-03-22
forum: General Help
---

### Post by sanitarium616 on 2012-03-22
i've just tried installing splashy via the software centre and got the following error:
installArchives() failed: Selecting previously deselected package tsconf.
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
(Reading database ... 183165 files and directories currently installed.)
Unpacking tsconf (from .../archives/tsconf_1.0-9_all.deb) ...
Selecting previously deselected package libts-0.0-0.
Unpacking libts-0.0-0 (from .../libts-0.0-0_1.0-9_i386.deb) ...
Selecting previously deselected package libdirectfb-1.2-9.
Unpacking libdirectfb-1.2-9 (from .../libdirectfb-1.2-9_1.2.10.0-4ubuntu3_i386.deb) ...
Selecting previously deselected package libdirectfb-extra.
Unpacking libdirectfb-extra (from .../libdirectfb-extra_1.2.10.0-4ubuntu3_i386.deb) ...
Selecting previously deselected package libsplashy1.
Unpacking libsplashy1 (from .../libsplashy1_0.3.13-5.1ubuntu1_i386.deb) ...
Selecting previously deselected package splashy.
Unpacking splashy (from .../splashy_0.3.13-5.1ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/splashy_0.3.13-5.1ubuntu1_i386.deb (--unpack):
 trying to overwrite '/etc/lsb-base-logging.sh', which is also in package lsb-base 4.0-0ubuntu16
No apport report written because MaxReports is reached already
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/splashy_0.3.13-5.1ubuntu1_i386.deb
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
Setting up tsconf (1.0-9) ...
Setting up libts-0.0-0 (1.0-9) ...
Setting up libdirectfb-1.2-9 (1.2.10.0-4ubuntu3) ...
Setting up libdirectfb-extra (1.2.10.0-4ubuntu3) ...
Setting up libsplashy1 (0.3.13-5.1ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

is there a way round this as i'd like to have a splash screen instead of the black screen menu on a distributable copy of my ubuntu 11.10 set up
any help would be appreatiated 
sani

---

