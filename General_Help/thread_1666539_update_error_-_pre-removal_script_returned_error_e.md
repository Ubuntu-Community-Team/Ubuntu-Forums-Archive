---
title: "update error - pre-removal script returned error exit status 126"
date: 2011-01-13
forum: General Help
---

### Post by r00r on 2011-01-13
Hi all,

On 10.10, I am getting the error below when running apt-get dist-upgrade and am at a loss at how to fix it.

Thanks for any help!

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  ubuntu-sso-client
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
14 not fully installed or removed.
Need to get 0B/29.2kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 213491 files and directories currently installed.)
Preparing to replace ubuntu-sso-client 1.0.7-0ubuntu1 (using .../ubuntu-sso-client_1.0.8-0ubuntu1_all.deb) ...
/var/lib/dpkg/info/ubuntu-sso-client.prerm: 6: update-python-modules: Permission denied
dpkg: warning: subprocess old pre-removal script returned error exit status 126
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: update-python-modules: Permission denied
dpkg: error processing /var/cache/apt/archives/ubuntu-sso-client_1.0.8-0ubuntu1_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 126
/var/lib/dpkg/info/ubuntu-sso-client.postinst: 28: update-python-modules: Permission denied
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 126
Errors were encountered while processing:
 /var/cache/apt/archives/ubuntu-sso-client_1.0.8-0ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

