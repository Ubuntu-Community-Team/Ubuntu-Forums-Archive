---
title: "Problem installing Amazon Downloader"
date: 2011-07-07
forum: General Help
---

### Post by partyk1d24 on 2011-07-07
When I try to install Amazon deb using...
~/Downloads$ sudo dpkg -i --force-architecture amazonmp3.deb

I get the following...
```

dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 195941 files and directories currently installed.)
Preparing to replace amazonmp3:i386 1.0.9-1 (using amazonmp3.deb) ...
Unpacking replacement amazonmp3:i386 ...
dpkg: dependency problems prevent configuration of amazonmp3:i386:
 amazonmp3:i386 depends on libgtkmm-2.4-1c2a.
 amazonmp3:i386 depends on libglademm-2.4-1c2a.
 amazonmp3:i386 depends on libboost-filesystem1.34.1; however:
  Package libboost-filesystem1.34.1:i386 is not configured yet.
 amazonmp3:i386 depends on libboost-regex1.34.1; however:
  Package libboost-regex1.34.1:i386 is not configured yet.
 amazonmp3:i386 depends on libboost-thread1.34.1; however:
  Package libboost-thread1.34.1:i386 is not configured yet.
 amazonmp3:i386 depends on libboost-iostreams1.34.1; however:
  Package libboost-iostreams1.34.1:i386 is not configured yet.
 amazonmp3:i386 depends on libboost-signals1.34.1; however:
  Package libboost-signals1.34.1:i386 is not configured yet.
 amazonmp3:i386 depends on libboost-date-time1.34.1; however:
  Package libboost-date-time1.34.1:i386 is not configured yet.
 amazonmp3:i386 depends on libcurl3; however:
 amazonmp3:i386 depends on libssl0.9.8; however:
 amazonmp3:i386 depends on xdg-utils; however:
dpkg: error processing amazonmp3:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Unknown media type in type 'interface/x-winamp-skin'
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 amazonmp3:i386

```

Any ideas!

---

### Post by Pard68 on 2011-07-07
Looks like you have some dependencies issues. Maybe you should get those dependencies before you retry installing Amazon.

---

