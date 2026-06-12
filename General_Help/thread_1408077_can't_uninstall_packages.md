---
title: "can't uninstall packages"
date: 2010-02-15
forum: General Help
---

### Post by jazz_vill on 2010-02-15
I wanted to uninstall a program say emacs for example. I cant uninstall it and during the process i get these errors.

```

jazz@jazz-laptop:~$ sudo apt-get -f remove emacs
[sudo] password for jazz: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package emacs is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
7 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up python-sip4 (4.9.1-snapshot-20091015-0ubuntu1) ...
/usr/sbin/update-python-modules: 11: import: not found
from: can't read /var/mail/optparse
from: can't read /var/mail/subprocess
from: can't read /var/mail/py_compile
/usr/sbin/update-python-modules: 15: Syntax error: word unexpected (expecting ")")
dpkg: error processing python-sip4 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python-qt4:
 python-qt4 depends on python-sip4 (>= 4.9); however:
  Package python-sip4 is not configured yet.
 python-qt4 depends on python-sip4 (<< 4.10); however:
  Package python-sip4 is not configured yet.
dpkg: error processing python-qt4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-kde4:
 python-kde4 depends on python-qt4 (>= 4.3-2ubuntu7.1); however:
  Package python-qt4 is not configured yet.
dpkg: error processing python-kde4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-workspace-data:
 kdebase-workspace-data depends on python-kde4 (>= 4:4.2.0); however:
  Package python-kde4 is not configured yet.
dpkg: error processing kdebase-workspace-data (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdebase-workspace-bin:
 kdebase-workspNo apport report written because the error message indicates its a followup error from a previous failure.
                                         No apport report written because the error message indicates its a followup error from a previous failure.
                                                                   No apport report written because MaxReports is reached already
                                                 No apport report written because MaxReports is reached already
                               No apport report written because MaxReports is reached already
             ace-bin depends on kdebase-workspace-data (= 4:4.3.2-0ubuntu7.1); however:
  Package kdebase-workspace-data is not configured yet.
dpkg: error processing kdebase-workspace-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of k3b:
 k3b depends on kdebase-workspace-bin; however:
  Package kdebase-workspace-bin is not configured yet.
dpkg: error processing k3b (--configure):
 dependency problems - leaving unconfigured
Setting up rhythmbox (0.12.5-0ubuntu5.2) ...
/usr/bin/update-gconf-defaults: 7: treefile: not found
/usr/bin/update-gconf-defaults: 9: import: not found
from: can't read /var/mail/optparse
/usr/bin/update-gconf-defaults: 12: Syntax error: "(" unexpected
dpkg: error processing rhythmbox (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Processing triggers for menu ...
Errors were encountered while processing:
 python-sip4
 python-qt4
 python-kde4
 kdebase-workspace-data
 kdebase-workspace-bin
 k3b
 rhythmbox

```

Please help I really want to uninstall some programs I don't need... thanks a lot in advance!

---

### Post by zvacet on 2010-02-16
First run this command

```
sudo dpkg --configure -a
```

You can uninstall packages with synaptic if you want to.

---

