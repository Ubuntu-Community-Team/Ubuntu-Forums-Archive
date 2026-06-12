---
title: "Cannot install KDE-DESKTOP"
date: 2009-11-12
forum: General Help
---

### Post by tobey1 on 2009-11-12
I was installing KDE desktop in Ubuntu 9.10 in my VM, and virtualbox crashed during the install.  I cannot get the install to resume again.  

when I type this (sudo apt-get install -f) as directed in other forums, I get the following.  Is there anyway to fix it?

dpkg: too many errors, stopping
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Errors were encountered while processing:
 kdepimlibs5
 libkdepim4
 libkontactinterfaces4
 akregator
 libtag-extras1
 amarok-utils
 libfftw3-3
 liblastfm0
 amarok
 libpolkit2
 libpolkit-dbus2
 libpolkit-grant2
 libpolkit-qt0
 libqt4-assistant
 libqt4-help
 libqt4-scripttools
 libqt4-test
 libqt4-xmlpatterns
 python-sip4
 python-qt4
 python-kde4
 apport-kde
 gdebi-kde
 install-package
 software-properties-kde
 apturl-kde
 jockey-kde
 libk3b6
 plasma-dataengines-workspace
 kdepim-runtime-libs4
 kdepim-runtime
 plasma-widgets-workspace
 policykit
 kdebase-workspace-bin
 k3b
 libkabcommon4
 libkleo4
 kaddressbook
 kdebluetooth
 kdepim-groupware
 kdepim-kresources
 kdepim-strigi-plugins
 kdepim-wizards
 kipi-plugins
 kmail
 knotes
 kontact
 libkopete4
 kopete
 korganizer
 ktimetracker
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by kio_http on 2009-11-12
type 

```
sudo dpkg
```

It should tell you depackage was interrupted and offer a command to fix

---

