---
title: "problem installing nfs-common"
date: 2010-10-09
forum: General Help
---

### Post by avee137 on 2010-10-09
Hello,
I need to install nfs-common package.when i do it using apt-get,i get following output:
```
avi@avi-laptop:~$ sudo apt-get install nfs-common
[sudo] password for avi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nfs-common is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nfs-common has no installation can
```when i try to install binaries from ubuntu repositories using GDebi,i get following error:

```
Error: Dependency is not satisfiable: sysvinit (>= 2.80-1)

```what should i do to come out of it?

---

### Post by clrg on 2010-10-09
That's because there is no such package in the default repositories:

```
$ apt-cache search sysvinit
acct - The GNU Accounting utilities for process and login accounting
sysvinit-utils - System-V-like utilities
sysvutils - System-V-like utilities (transitional package)
runit-services - a UNIX init scheme with service supervision (services)
$ 

```

I don't know why its asking for 'sysvinit'. Ubuntu uses Upstart, not System V-style init scripts.

What happens when you try to mount a NFS share? Eg

```
sudo mount -t nfs host:/share/path /mnt
```

---

