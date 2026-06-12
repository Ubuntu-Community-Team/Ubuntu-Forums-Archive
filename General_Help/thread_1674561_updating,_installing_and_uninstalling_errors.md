---
title: "updating, installing and uninstalling errors"
date: 2011-01-24
forum: General Help
---

### Post by Bradtek on 2011-01-24
Trying to remove libre office results in


An unhandlable error occured

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.


```
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 769, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 948, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the chromium-browser package. This might mean you need to manually fix this package.

```


trying to remove chromium-browser results in

Package operation failed

```
The installation or removal of a software package failed.


installArchives() failed: (Reading database ... 
dpkg: warning: files list file for package `ttf-opensymbol' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreoffice-calc' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreoffice-draw' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreoffice-gtk' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreoffice-style-galaxy' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreoffice-report-builder-bin' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `chromium-browser' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreoffice-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreoffice-emailmerge' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreoffice-base' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreoffice-gnome' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreoffice-filter-binfilter' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreoffice-base-core' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreoffice-filter-mobiledev' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreoffice-java-common' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreoffice-writer' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreoffice-style-tango' missing, assuming package has no files currently installed.

dpkg: warning: files list file for package `libreoffice-impress' missing, assuming package has no files currently installed.

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
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 files list file for package `python-uno' contains empty filename
dpkg: dependency problems prevent configuration of frostwire:
 frostwire depends on default-jre-headless; however:
  Package default-jre-headless is not installed.
 frostwire depends on default-jre; however:
  Package default-jre is not installed.
dpkg: error processing frostwire (--configure):
 dependency problems - leaving unconfigured
Setting up man-db (2.5.7-4) ...
dpkg: error processing man-db (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of chromium-browser-inspector:
 chromium-browser-inspector depends on chromium-browser; however:
  Package chromium-browser is not installed.
dpkg: error processing chromium-browser-inspector (--configure):
 dependency problems - leaving unconfigured
```


I've tried software centre, synaptic and terninal
all result in errors.

Any idea where I need to start to solve this ?

---

