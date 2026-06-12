---
title: "Unable to upgrade firefox"
date: 2012-07-30
forum: General Help
---

### Post by Ansowi on 2012-07-30
```

bui@bluefly:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  firefox
Suggested packages:
  latex-xft-fonts
The following packages will be upgraded:
  firefox
1 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
214 not fully installed or removed.
Need to get 0 B/18.9 MB of archives.
After this operation, 1,698 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 128038 files and directories currently installed.)
Preparing to replace firefox 11.0+build1-0ubuntu4 (using .../firefox_14.0.1+build1-0ubuntu0.12.04.1_i386.deb) ...
Unpacking replacement firefox ...
dpkg-deb (subprocess): failed to read on buffer copy for failed to write to pipe in copy: Input/output error
dpkg-deb: error: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/firefox_14.0.1+build1-0ubuntu0.12.04.1_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/firefox/libnss3.so'
Please restart all running instances of firefox, or you will experience problems.
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/firefox_14.0.1+build1-0ubuntu0.12.04.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
bui@bluefly:~$ 

```

How can I solve this? And yes, I did upgrade while Firefox was closed.

---

### Post by Ansowi on 2012-07-30
Managed to solve myself. Ran apt-get clean and downloaded the package again.

---

