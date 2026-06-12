---
title: "Help -  Error updating liblwres40"
date: 2010-01-27
forum: General Help
---

### Post by Magrovsky on 2010-01-27
Hello, first time posting. I've been using ubuntu for the last 2 years, since my vista went kapoft, mainly for browsing/word editing. Never had any problem until this morning. 

The update manager refused to install the package liblwres40. the error given was:

```
E: /var/cache/apt/archives/liblwres40_1%3a9.5.1.dfsg.P2-1ubuntu0.4_i386.deb: unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/md5sums'
```

i did an apt-get -f install to get the full error message, and i got this:

```

paulo@paulo-desktop:~$ sudo apt-get -f  install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdns45
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  liblwres40
The following packages will be upgraded:
  liblwres40
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/44.6kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 160036 files and directories currently installed.)
Preparing to replace liblwres40 1:9.5.1.dfsg.P2-1ubuntu0.3 (using .../liblwres40_1%3a9.5.1.dfsg.P2-1ubuntu0.4_i386.deb) ...
Unpacking replacement liblwres40 ...
dpkg (subprocess): unable to execute old post-removal script: Permission denied
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
dpkg: error processing /var/cache/apt/archives/liblwres40_1%3a9.5.1.dfsg.P2-1ubuntu0.4_i386.deb (--unpack):
 unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/md5sums': Is a directory
Errors were encountered while processing:
 /var/cache/apt/archives/liblwres40_1%3a9.5.1.dfsg.P2-1ubuntu0.4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

i use Ubuntu 9.04.

Any ideas? should i do a clean reinstall, like a good windows user, or maybe upgrade to 9.10 and hope this error go away, or even completely ignore this package and go on with my life?

---

