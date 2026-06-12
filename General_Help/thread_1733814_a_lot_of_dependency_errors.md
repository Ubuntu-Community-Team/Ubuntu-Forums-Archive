---
title: "a lot of dependency errors"
date: 2011-04-19
forum: General Help
---

### Post by stber321 on 2011-04-19
I installed Plymouth manager and played around a little bit. then I rebooted and decieded i did not like the boot splash I applied. it would not open. i added the Plymouth PPA and ran "sudo aptitude update" and "sudo aptitude dist-upgrade". i unplugged the computer while running dist-upgrade. i booted only to find no boot slash, GTK all mesed up and compiz not working. the output of ```
sudo aptitude -f install
``` is ```

The following partially installed packages will be configured:
  language-selector language-selector-common language-selector-qt 
  oem-config oem-config-gtk ubiquity ubiquity-frontend-gtk 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up language-selector-common (0.6.7) ...
dpkg: error processing language-selector-common (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on language-selector-common (= 0.6.7); however:
  Package language-selector-common is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector-qt:
 language-selector-qt depends on language-selector-common (= 0.6.7); however:
  Package language-selector-common is not configured yet.
dpkg: error processing language-selector-qt (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of ubiquity:
 ubiquity depends on language-selector-common (>= 0.4.16); however:
  Package language-selector-common is not configured yet.
dpkg: error processing ubiquity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubiquity-frontend-gtk:
 ubiquity-frontend-gtk depends on ubiquity (= 2.4.8-1mint3); however:
  Package ubiquity is not configured yet.
dpkg: error processing ubiquity-frontend-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of oem-config:
 oem-config depends on ubiquity (= 2.4.8-1mint3); however:
  Package ubiquity is not configured yet.
dpkg: error processing oem-config (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          dpkg: dependency problems prevent configuration of oem-config-gtk:
 oem-config-gtk depends on oem-config (= 2.4.8-1mint3); however:
  Package oem-config is not configured yet.
 oem-config-gtk depends on ubiquity-frontend-gtk (= 2.4.8-1mint3); however:
  Package ubiquity-frontend-gtk is not configured yet.
dpkg: error processing oem-config-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Processing triggers for python-central ...
Errors were encountered while processing:
 language-selector-common
 language-selector
 language-selector-qt
 ubiquity
 ubiquity-frontend-gtk
 oem-config
 oem-config-gtk
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up language-selector-common (0.6.7) ...
dpkg: error processing language-selector-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on language-selector-common (= 0.6.7); however:
  Package language-selector-common is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-selector-qt:
 language-selector-qt depends on language-selector-common (= 0.6.7); however:
  Package language-selector-common is not configured yet.
dpkg: error processing language-selector-qt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubiquity:
 ubiquity depends on language-selector-common (>= 0.4.16); however:
  Package language-selector-common is not configured yet.
dpkg: error processing ubiquity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubiquity-frontend-gtk:
 ubiquity-frontend-gtk depends on ubiquity (= 2.4.8-1mint3); however:
  Package ubiquity is not configured yet.
dpkg: error processing ubiquity-frontend-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of oem-config:
 oem-config depends on ubiquity (= 2.4.8-1mint3); however:
  Package ubiquity is not configured yet.
dpkg: error processing oem-config (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of oem-config-gtk:
 oem-config-gtk depends on oem-config (= 2.4.8-1mint3); however:
  Package oem-config is not configured yet.
 oem-config-gtk depends on ubiquity-frontend-gtk (= 2.4.8-1mint3); however:
  Package ubiquity-frontend-gtk is not configured yet.
dpkg: error processing oem-config-gtk (--configure):
 dependency problems - leaving unconfigured
Processing triggers for python-central ...
Errors were encountered while processing:
 language-selector-common
 language-selector
 language-selector-qt
 ubiquity
 ubiquity-frontend-gtk
 oem-config
 oem-config-gtk


```i would be verry appricaitive of those who would help me

---

### Post by mikewhatever on 2011-04-19
Unplugging the computer while running dist-upgrade was a bad idea, why did you do it? You might wanna repeat it, but skip the unplugging part.

---

### Post by stber321 on 2011-04-19
> **mikewhatever said:**
> Unplugging the computer while running dist-upgrade was a bad idea, why did you do it? You might wanna repeat it, but skip the unplugging part.

1. it was not intentional
2. i have tried, it will give me the exact same output. even when installing a package

i have also tried apt-get. not just aptitude

---

### Post by plucky on 2011-04-19
> **stber321 said:**
> 1. it was not intentional
2. i have tried, it will give me the exact same output. even when installing a package

i have also tried apt-get. not just aptitude

Try ```
sudo dpkg --configure -a
```

Then ```
sudo apt-get dist-upgrade
```

Good Luck

---

### Post by stber321 on 2011-04-19
> **plucky said:**
> Try ```
sudo dpkg --configure -a
```Then ```
sudo apt-get dist-upgrade
```Good Luck

same output as above

---

### Post by reve_etrange on 2011-04-19
I am experiencing the same problem...only my issue began following a failure dialog from update-manager.  The system hasn't been brought down yet.

---

### Post by spyd4r on 2011-04-20
i've come across the same issue, doesn't appear to be related to you unplugging your system during a dist-upgrade.

```
$ sudo apt-get install language-selector-common 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
language-selector-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up language-selector-common (0.6.7) ...
dpkg: error processing language-selector-common (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of language-selector:
 language-selector depends on language-selector-common (= 0.6.7); however:
  Package language-selector-common is not configured yet.
dpkg: error processing language-selector (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Processing triggers for python-central ...
Errors were encountered while processing:
 language-selector-common
 language-selector
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by tredegar on 2011-04-20
This seems to be a bug with language-selector-common updates.
It is discussed here [here]("http://ubuntuforums.org/showthread.php?t=1733722"), and there is a solution.

---

### Post by stber321 on 2011-04-20
> **tredegar said:**
> This seems to be a bug with language-selector-common updates.
It is discussed here [here]("http://ubuntuforums.org/showthread.php?t=1733722"), and there is a solution.

that did not fix anything i am still doomed, I guess I will just reinstall(again)...

---

