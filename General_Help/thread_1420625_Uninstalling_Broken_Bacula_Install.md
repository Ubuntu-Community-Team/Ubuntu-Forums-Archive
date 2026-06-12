---
title: "Uninstalling Broken Bacula Install"
date: 2010-03-03
forum: General Help
---

### Post by Cerin on 2010-03-03
Something broke while I tried to install Bacula, and now I'm unable to uninstall the bacula-director-pgsql package.

This is the output of apt-get when I try to uninstall:
```
$ sudo apt-get remove bacula-director-pgsql
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqwt5-qt4 dbconfig-common mtx libqt4-svg bsd-mailx mailx
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bacula-director-pgsql
0 upgraded, 0 newly installed, 1 to remove and 72 not upgraded.
1 not fully installed or removed.
After this operation, 1,270kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 226088 files and directories currently installed.)
Removing bacula-director-pgsql ...
invoke-rc.d: unknown initscript, /etc/init.d/bacula-director not found.
dpkg: error processing bacula-director-pgsql (--remove):
 subprocess installed pre-removal script returned error exit status 100
dbconfig-common: flushing administrative password
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 100
Errors were encountered while processing:
 bacula-director-pgsql
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Does anyone know what this means? How do I force apt-get to remove the package?

My original plan was to install Bacula with the Postgres storage backend. The installer couldn't connect to Postgres, so I'm assuming that's what broke the process. Regardless, nothing was installed in my Postgres DB, so the package shouldn't have to do anything. Any help removing this broken package is greatly appreciated.

Regards,
Chris

---

### Post by Cerin on 2010-03-03
Spoke too soon. Trying a different Google query finally found me [http://www.mail-archive.com/ubuntu-server-bugs@lists.ubuntu.com/msg25630.html](http://www.mail-archive.com/ubuntu-server-bugs@lists.ubuntu.com/msg25630.html)

Apparently, the failed uninstall removed some files prematurely, including:
touch /etc/init.d/bacula-director

After re-adding that, the purge succeeded. Would have been nice if apt-get had told me this in the first place.

---

