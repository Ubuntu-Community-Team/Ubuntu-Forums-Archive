---
title: "Crash while installing KDE with apt-get"
date: 2009-06-27
forum: General Help
---

### Post by vkazemi on 2009-06-27
ubuntu crashed while installing KDE with apt-get, and now I can't install or remove anything with the package manager. Does anybody know how can I fix this?

```
apt-get -f install kde
Reading package lists... Done
Building dependency tree       
Reading state information... Done
kde is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
14 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up kwalletmanager (4:4.2.2-0ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing kwalletmanager (--configure):
 subprocess post-installation script returned error exit status 2
Setting up okteta (4:4.2.2-0ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing okteta (--configure):
 subprocess post-installation script returned error exit status 2
Setting up superkaramba (4:4.2.2-0ubuntu2) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing superkaramba (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of kdeutils:
 kdeutils depends on kwalletmanager (>= 4:4.2.2-0ubuntu2); however:
  Package kwalletmanager is not configured yet.
 kdeutils depends on okteta (>= 4:4.2.2-0ubuntu2); however:
  Package okteta is not configured yet.
 kdeutils depends on superkaramba (>= 4:4.2.2-0ubuntu2); however:
  Package superkaramba is not configured yet.
dpkg: error processing kdeutils (--configure):
 dependency problems - leaving unconfigured
Setting up kimagemapeditor-kde4 (4:4.2.2-0ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing kimagemapeditor-kde4 (--configure):
 subprocess post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up libtidy-0.99-0 (20081224cvs-1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libtidy-0.99-0 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of klinkstatus-kde4:
 klinkstatus-kde4 depends on libtidy-0.99-0; however:
  Package libtidy-0.99-0 is not configured yet.
dpkg: error processing klinkstatus-kde4 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kdewebdev-kde4:
 kdewebdev-kde4 depends on kimagemapeditor-kde4 (>= 4:4.2.2-0ubuntu1); however:
  Package kimagemapeditor-kde4 is not configured yet.
 kdewebdev-kde4 depends on klinkstatus-kde4 (>= 4:4.2.2-0ubuntu1); however:
  Package klinkstatus-kde4 is not configured yet.
dpkg: error processing kdewebdev-kde4 (--configure):
 dependency problems - leaving unconfigured
Setting up libkexiv2-7 (4:4.2.2-0ubuntu2) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libkexiv2-7 (--configure):
 subprocess post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up kdeplasma-addons-data (4:4.2.2-0ubuntu1) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing kdeplasma-addons-data (--configure):
 subprocess post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kdeplasma-addons:
 kdeplasma-addons depends on libkexiv2-7; however:
  Package libkexiv2-7 is not configured yet.
 kdeplasma-addons depends on kdeplasma-addons-data (= 4:4.2.2-0ubuntu1); however:
  Package kdeplasma-addons-data is not configured yet.
dpkg: error processing kdeplasma-addons (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kde:
 kde depends on kdeutils (>= 4:4.1.1); however:
  Package kdeutils is not configured yet.
 kde depends on kdewebdev-kde4 (>= 4:4.1.1); however:
  Package kdewebdev-kde4 is not configured yet.
 kde depends on kdeplasma-addons (>= 4:4.1.1); however:
  Package kdeplasma-addons is not configured yet.
dpkg: error processing kde (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up libkonq5 (4:4.2.2-0ubuntu4) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing libkonq5 (--configure):
 subprocess post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kdebase-plasma:
 kdebase-plasma depends on libkonq5; however:
  Package libkonq5 is not configured yet.
dpkg: error processing kdebase-plasma (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 kwalletmanager
 okteta
 superkaramba
 kdeutils
 kimagemapeditor-kde4
 libtidy-0.99-0
 klinkstatus-kde4
 kdewebdev-kde4
 libkexiv2-7
 kdeplasma-addons-data
 kdeplasma-addons
 kde
 libkonq5
 kdebase-plasma
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

