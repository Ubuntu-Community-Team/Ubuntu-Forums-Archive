---
title: "APT strange problem"
date: 2011-08-07
forum: General Help
---

### Post by jjasper22 on 2011-08-07
Hi !  I'm relative new Linux/Ubuntu user and run into strange problem with APT - it won't update anymore :( :(  

The Ubuntu 'Update Manager' itself is running and I could click on 'Check' and/or may be change 'sources' and program generally looking as it working. All the bad stuff happens when I click on 'Install updates'. Immediately pop-up dialog with 'An unhandlable error occured' and this is error itself:

```

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:Method  has died unexpectedly!, E:Sub-process  returned an error code (100), E:Method /usr/lib/apt/methods/ did not start correctly

```

If I run apt-get manually - I could get the list of programs to update and run all other functions but not 'upgrade' or 'install' - this is the output:

```

alex@alex-ubuntu:/$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gnome-user-guide google-chrome-stable libsmbclient libwbclient0 lintian samba samba-common
  samba-common-bin smbclient
9 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Failed to exec method /usr/lib/apt/methods/
E: Method  has died unexpectedly!
E: Sub-process  returned an error code (100)
E: Method /usr/lib/apt/methods/ did not start correctly
alex@alex-ubuntu:/$

```

Here is my configuration:
Linux alex-ubuntu 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty

If you need more information just message me.

Thanks

---

### Post by allwimb on 2011-08-07
try doing apt-get purge and then do your apt-get install

[spring login]("http://www.java-forums.org/blogs/spring-framework/531-login-forms-spring-security.html")

---

