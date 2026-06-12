---
title: "failed installation"
date: 2010-05-04
forum: General Help
---

### Post by ssj6akshat on 2010-05-04
i was installing gnome-office and there was a blackout in my area so it was interrupted in the middle when I try to install it again it gives me this message

```
(Reading database ... 176640 files and directories currently installed.)
Unpacking gnome-office (from .../gnome-office_1%3a2.28+1ubuntu3_all.deb) ...
Setting up libwv-1.2-3 (1.2.4-2ubuntu3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libwv-1.2-3 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libabiword-2.8:
 libabiword-2.8 depends on libwv-1.2-3 (>= 1.2.4); however:
  Package libwv-1.2-3 is not configured yet.
dpkg: error processing libabiword-2.8 (--configure):
 dependency problems - leaving unconfigured
Setting up libaiksaurus-1.2-0c2a (1.2.1+dev-0.12-6build1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libaiksaurus-1.2-0c2a (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libaiksaurusgtk-1.2-0c2a:
 libaiksaurusgtk-1.2-0c2a depends on libaiksaurus-1.2-0c2a (>= 1.2.1+dev-0.12); however:
  Package libaiksaurus-1.2-0c2a is not configured yet.
dpkg: error processing libaiksaurusgtk-1.2-0c2a (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of abiword:
 abiword depends on libabiword-2.8 (= 2.8.2-2ubuntu1); however:
  Package libabiword-2.8 is not configured yet.
 abiword depends on libaiksaurus-1.2-0c2a (>= 1.2.1+dev-0.12); however:
  Package libaiksaurus-1.2-0c2a is not configured yet.
 abiword depends on libaiksaurusgtk-1.2-0c2a (>= 1.2.1+dev-0.12); however:
  Package libaiksaurusgtk-1.2-0c2a is not configured yet.
 abiword depends on liNo apport report written because MaxReports is reached already
    No apport report written because MaxReports is reached already
                                                                  No apport report written because MaxReports is reached already
                                                No apport report written because MaxReports is reached already
                              No apport report written because MaxReports is reached already
            bwv-1.2-3 (>= 1.2.4); however:
  Package libwv-1.2-3 is not configured yet.
dpkg: error processing abiword (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of abiword-plugin-grammar:
 abiword-plugin-grammar depends on libabiword-2.8 (= 2.8.2-2ubuntu1); however:
  Package libabiword-2.8 is not configured yet.
 abiword-plugin-grammar depends on libwv-1.2-3 (>= 1.2.4); however:
  Package libwv-1.2-3 is not configured yet.
 abiword-plugin-grammar depends on abiword (= 2.8.2-2ubuntu1); however:
  Package abiword is not configured yet.
dpkg: error processing abiword-plugin-grammar (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of abiword-plugin-mathview:
 abiword-plugin-mathview depends on libabiword-2.8 (= 2.8.2-2ubuntu1); however:
  Package libabiword-2.8 is not configured yet.
 abiword-plugin-mathview depends on libwv-1.2-3 (>= 1.2.4); however:
  Package libwv-1.2-3 is not configured yet.
 abiword-plugin-mathview depends on abiword (= 2.8.2-2ubuntu1); however:
  Package abiword is not configured yet.
dpkg: error processing abiword-plugin-mathview (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-office:
 gnome-office depends on abiword; however:
  Package abiword is not configured yet.
dpkg: error processing gnome-office (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libwv-1.2-3
 libabiword-2.8
 libaiksaurus-1.2-0c2a
 libaiksaurusgtk-1.2-0c2a
 abiword
 abiword-plugin-grammar
 abiword-plugin-mathview
 gnome-office
E: Sub-process /usr/bin/dpkg returned an error code (1)
akshat@akshat-desktop:~$ 
```

---

