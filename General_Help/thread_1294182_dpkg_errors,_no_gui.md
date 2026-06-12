---
title: "dpkg errors, no gui"
date: 2009-10-18
forum: General Help
---

### Post by scambro on 2009-10-18
I haven't been able to get gnome up and running for about 2 months and just decided to work on it a bit more this weekend.  I also have problems installing anything.  The last thing I recall doing on this server, was installing a lot of updates.  When I try to install something now I get the following errors:

```
$ sudo apt-get install gzip
Reading package lists... Done
Building dependency tree
Reading state information... Done
gzip is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 45 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up xulrunner-1.9 (1.9.0.14+build2+nobinonly-0ubuntu0.8.10.1) ...
/usr/lib/xulrunner-1.9.0.14/xulrunner-bin: symbol lookup error: /usr/lib/libgio-2.0.so.0: undefined symbol: g_thread_gettime
dpkg: error processing xulrunner-1.9 (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of firefox-3.0:
 firefox-3.0 depends on xulrunner-1.9 (>= 1.9.0.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing firefox-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-branding:
 firefox-3.0-branding depends on firefox-3.0 (= 3.0.14+build2+nobinonly-0ubuntu0.8.10.1); however:
  Package firefox-3.0 is not configured yet.
dpkg: error processing firefox-3.0-branding (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.0; however:
  Package firefox-3.0 is not configured yet.
 firefox depends on firefox-3.0-branding; however:
  Package firefox-3.0-branding is not configured yet.
dpkg: error processing firefox (--configure):
dNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                            No apport report written because the error message indicates its a followup error from a previous failure.
                                       No apport report written because MaxReports is reached already
                                                                                                     No apport report written because MaxReports is reached already
                                                                                                                                                                   No apport report written because MaxReports is reached already
                                                  No apport report written because MaxReports is reached already
                                                                                                                ependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on xulrunner-1.9 (= 1.9.0.14+build2+nobinonly-0ubuntu0.8.10.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on firefox-3.0 (= 3.0.14+build2+nobinonly-0ubuntu0.8.10.1); however:
  Package firefox-3.0 is not configured yet.
 firefox-3.0-gnome-support depends on xulrunner-1.9-gnome-support (>= 1.9~b4~); however:
  Package xulrunner-1.9-gnome-support is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.0-gnome-support; however:
  Package firefox-3.0-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xulrunner-1.9
 firefox-3.0
 firefox-3.0-branding
 firefox
 xulrunner-1.9-gnome-support
 firefox-3.0-gnome-support
 firefox-gnome-support
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Some searching of similar errors on google didn't turn up a whole lot.  Any ideas of where to start with this one?  Thanks!

---

### Post by scambro on 2009-10-19
Any ideas?  I'm hoping there's a key in the error message that means something to someone.  Thanks!

---

