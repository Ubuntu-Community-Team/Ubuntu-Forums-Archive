---
title: "aptitude/apt-get fails to remove/install/reinstall a package"
date: 2009-12-31
forum: General Help
---

### Post by Visko on 2009-12-31
I had a HDD fail on me, and since then I always get notices from aptitude that there is a package named 'python-twisted-web' that is in a very bad state. Running dpkg -C produces:

```
The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 python-twisted-web   An HTTP protocol implementation together with clients and ...
```

Okay, let's do an aptitude reinstall python-twisted-web:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages will be REINSTALLED:
  python-twisted-web
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0B/391kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 15%
dpkg: warning: files list file for package `python-twisted-web' missing, assuming package has no files currently installed.
(Reading database ... 64562 files and directories currently installed.)
Preparing to replace python-twisted-web 8.2.0-2ubuntu1 (using .../python-twisted-web_8.2.0-2ubuntu1_all.deb) ...
pycentral: pycentral pkgremove: package python-twisted-web is not installed
pycentral pkgremove: package python-twisted-web is not installed
dpkg: warning: old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
pycentral: pycentral pkgremove: package python-twisted-web is not installed
pycentral pkgremove: package python-twisted-web is not installed
dpkg: error processing /var/cache/apt/archives/python-twisted-web_8.2.0-2ubuntu1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
pycentral: pycentral pkginstall: package python-twisted-web is not installed
pycentral pkginstall: package python-twisted-web is not installed
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/python-twisted-web_8.2.0-2ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
dpkg: error processing python-twisted-web (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Errors were encountered while processing:
 python-twisted-web
Reading package lists... /snip/
```

Let's remove it then, aptitude remove python-twisted-web:

```
/snip/
The following packages will be REMOVED:
  python-twisted-web
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 1,806kB will be freed.
Writing extended state information... Done
dpkg: error processing python-twisted-web (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 python-twisted-web
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... /snip/
```

Can someone suggest a solution?

---

### Post by Brandon Williams on 2009-12-31
Try removing all of the dpkg/info files associated with python-twisted-web.
```
sudo rm -f /var/lib/dpkg/info/python-twisted-web*
```

After that, try to reinstall the package again.

---

