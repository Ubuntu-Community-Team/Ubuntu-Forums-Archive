---
title: "Oracle 10g XE in Ubuntu Natty"
date: 2011-07-22
forum: General Help
---

### Post by biggie_ on 2011-07-22
Hello,

I'm following this guide: [http://littlebrain.org/2008/05/12/how-to-install-oracle-xe-in-ubuntu-64-bit/](http://littlebrain.org/2008/05/12/how-to-install-oracle-xe-in-ubuntu-64-bit/)

My problem is:

```
# dpkg --force-all --ignore-depends=libc6 -i oracle-xe-universal_10.2.0.1-1.0_i386.deb 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 178649 files and directories currently installed.)
Preparing to replace oracle-xe-universal:i386 10.2.0.1-1.0 (using oracle-xe-universal_10.2.0.1-1.0_i386.deb) ...
Unpacking replacement oracle-xe-universal:i386 ...
dpkg: dependency problems prevent configuration of oracle-xe-universal:i386:
 oracle-xe-universal:i386 depends on libc6 (>= 2.3.2).
dpkg: error processing oracle-xe-universal:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for python-support ...
Errors were encountered while processing:
 oracle-xe-universal:i386
```Why --force-all doesn't work?

Thank you for help.

EDIT:

Version of my libc6 is higher than requested by package:
```
# dpkg -l |grep libc6
ii  libc6                                 2.13-0ubuntu13                             Embedded GNU C Library: Shared libraries
ii  libc6-dev                             2.13-0ubuntu13                             Embedded GNU C Library: Development Libraries and Header Files
ii  libc6-i386                            2.13-0ubuntu13                             Embedded GNU C Library: 32-bit shared libraries for AMD64
```

---

