---
title: "APT strange problem"
date: 2011-08-10
forum: General Help
---

### Post by jjasper22 on 2011-08-10
Hi

Suddenly apt stop working :( This is an error:

```

alex@alex-ubuntu:~$ sudo apt-get upgrade
[sudo] password for alex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  adobe-flash-properties-gtk adobe-flashplugin ecryptfs-utils gnome-user-guide
  google-chrome-stable libecryptfs0 libsmbclient libwbclient0 lintian samba
  samba-common samba-common-bin smbclient
13 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Failed to exec method /usr/lib/apt/methods/
E: Method  has died unexpectedly!
E: Sub-process  returned an error code (100)
E: Method /usr/lib/apt/methods/ did not start correctly

```


The same (?) error I receive in 'Update manager' utility:

An unhandlable error occurred

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


Here is my Ubuntu:

uname -a
Linux alex-ubuntu 2.6.38-10-generic #46-Ubuntu SMP Tue Jun 28 15:05:41 UTC 2011 i686 i686 i386 GNU/Linux

lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty

---

### Post by jamie1990 on 2011-08-10
I am experiencing a similar problem, have your desktop links also stopped working?

---

### Post by Bucky Ball on 2011-08-10
```
sudo apt-get update
sudo apt-get upgrade

```
Don't worry about the errors. Any luck?

---

### Post by jjasper22 on 2011-08-10
> **Bucky Ball said:**
> ```
sudo apt-get update
sudo apt-get upgrade

```Don't worry about the errors. Any luck?


apt-get update  <- does working. I even receive the list of all packages that need to be updated but I could not install them :( because 'apt-get upgrade' doesn't work with error above :( 

 I even re-install the apt-get with:
```

sudo apt-get install --reinstall apt

```

but it doesn't help. It fails with the same error

---

### Post by jjasper22 on 2011-08-11
For now I partially solved the problem: I installed some of the packages manually - I run 'apt-get install <package>' individually for every package and it does work. 

 One of the packages named: 'lintian' could not be installed anyway with above error as in first post.

---

### Post by jjasper22 on 2011-08-11
Yes - that's was a problem - broken/damaged package. After I remove this 'lintian' package from updating - everything went back to normal.

---

