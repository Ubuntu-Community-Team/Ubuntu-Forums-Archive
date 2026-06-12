---
title: "Bugs resulting in abnormal aptitude behaviour"
date: 2009-07-08
forum: General Help
---

### Post by merciadriluca on 2009-07-08
Hello,

As stated in bugs [https://bugs.launchpad.net/ubuntu/+source/m4/+bug/382790]("https://bugs.launchpad.net/ubuntu/+source/m4/+bug/382790") and [https://bugs.launchpad.net/ubuntu/+source/smartcard/+bug/375467]("https://bugs.launchpad.net/ubuntu/+source/smartcard/+bug/375467"), I am encountering various errors coming from aptitude.

The most often, I receive, e.g. when using ```
sudo apt-get upgrade
```:
```

$ sudo apt-get upgrade
[sudo] password for merciadriluca: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
7 not fully installed or removed.
Need to get 0B/218kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 265076 files and directories currently installed.)
Preparing to replace m4 1.4.11-1 (using .../archives/m4_1.4.11-1_i386.deb) ...
install-info: No dir file specified; try --help for more information.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
install-info: No dir file specified; try --help for more information.
dpkg: error processing /var/cache/apt/archives/m4_1.4.11-1_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
install-info: unrecognised option `--description=The GNU m4 macro preprocessor.'
	Try `install-info --help' for a complete list of options.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/m4_1.4.11-1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What can I do? Any help would me much appreciated.

---

