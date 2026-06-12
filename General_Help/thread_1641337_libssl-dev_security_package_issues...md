---
title: "libssl-dev security package issues.."
date: 2010-12-08
forum: General Help
---

### Post by haightc on 2010-12-08
SO it would apprear I am having issues with this latest package update and now I am stucks.   Help greatly appreciated...  here is what my console gives me...

cliffordh@MadHatter:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libssl-dev
The following packages will be upgraded:
  libssl-dev
1 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
Need to get 0B/2,013kB of archives.
After this operation, 28.7kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 306195 files and directories currently installed.)
Preparing to replace libssl-dev 0.9.8o-1ubuntu4.2 (using .../libssl-dev_0.9.8o-1ubuntu4.3_i386.deb) ...
Unpacking replacement libssl-dev ...
dpkg: error processing /var/cache/apt/archives/libssl-dev_0.9.8o-1ubuntu4.3_i386.deb (--unpack):
 unable to make backup link of `./usr/include/openssl/tls1.h' before installing new version: Operation not permitted
No apport report written because MaxReports is reached already
                                                              Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libssl-dev_0.9.8o-1ubuntu4.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

