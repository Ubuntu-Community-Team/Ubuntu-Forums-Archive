---
title: "kde-libs wants to be updated AND installed"
date: 2009-09-30
forum: General Help
---

### Post by NOT_Skeletor on 2009-09-30
I cannot get rid of this error, and I am unable to install (or update) anything.

For anything I attempt to install, I get this:

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libvncserver0 rdate update-inetd localechooser-data libdebconfclient0
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  kdelibs-data
The following NEW packages will be installed:
  libxp6
The following packages will be upgraded:
  kdelibs-data

```

And then the errors:

```

Preparing to replace kdelibs-data 4:3.5.10-0ubuntu6.2 (using .../kdelibs-data_4%3a3.5.10-0ubuntu6.2_all.deb) ...
dpkg (subprocess): unable to execute new pre-installation script: Permission denied
dpkg: error processing /var/cache/apt/archives/kdelibs-data_4%3a3.5.10-0ubuntu6.2_all.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
dpkg (subprocess): unable to execute new post-removal script: Permission denied
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/kdelibs-data_4%3a3.5.10-0ubuntu6.2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I have no clue why kdelibs-data needs to be both installed and upgraded. I have done an update, cleaned out /var/cache/apt/archives, apt-get clean, remove, purge, renamed the info dir and created a new one, and nothing I do will get rid of kdelibs-data. The first errors I got before doing all that was:

```

dpkg: serious warning: file list file for package 'kdelibs-data' missing, assuming package has no files currently installed

``` 

Any ideas at all how I can get rid of this? All kdelibs was being used for was mythbrowser so it is not being used anywhere else.

---

