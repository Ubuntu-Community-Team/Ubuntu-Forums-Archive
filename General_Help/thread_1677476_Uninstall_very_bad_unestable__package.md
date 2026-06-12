---
title: "Uninstall very bad unestable  package"
date: 2011-01-28
forum: General Help
---

### Post by ivanp on 2011-01-28
Hello,

I have installed, actually just tried to, BSecPKLinux-2.0.0.0007 as token utility, but the attempt screwed my synaptic. I'm using a ubuntu 10.10

While running the install file,  a package failed to install and from then on I was never able to fix this. the package is rnboifd. When i try to uninstall it or purge it using dpkg it complains it is in a "very bad inestable state" and should reinstalled. when trying to reinstall fails 
```
sudo dpkg --install rnboifd-2.0.0-7.i586.deb 
Selecting previously deselected package rnboifd.
(Reading database ... 
dpkg: warning: files list file for package `rnboifd' missing, assuming package has no files currently installed.
(Reading database ... 185266 files and directories currently installed.)
Preparing to replace rnboifd 2.0.0-7 (using rnboifd-2.0.0-7.i586.deb) ...
Unpacking replacement rnboifd ...
Setting up rnboifd (2.0.0-7) ...
dpkg: error processing rnboifd (--install):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 rnboifd

```

I also restarted in safe mode and run with repair broken package to get the same message, can't uninstall or fix, need to reinstall.

querying the status it shows is half installed, but can't remove it can't reinstall it. In order to removed I tough doing it by hand, so queried all files the package used and deleted them

```
sudo dpkg-query -L rnboifd
```

it remains as a half-installed package...
how could I remove this package?

---

### Post by ivanp on 2011-02-07
The answer lies in this post [http://ubuntuforums.org/showpost.php?p=7972472&postcount=10](http://ubuntuforums.org/showpost.php?p=7972472&postcount=10)

---

