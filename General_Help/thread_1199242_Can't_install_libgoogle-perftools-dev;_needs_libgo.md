---
title: "Can't install libgoogle-perftools-dev; needs libgoogle-perftools0 0.98-1ubuntu1"
date: 2009-06-28
forum: General Help
---

### Post by yang on 2009-06-28
For some reason, the dependencies with libgoogle-perftools* seem to be broken:

```

$ sudo aptitude install libgoogle-perftools-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
The following packages are BROKEN:
  libgoogle-perftools-dev
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 473kB of archives. After unpacking 1499kB will be used.
The following packages have unmet dependencies:
  libgoogle-perftools-dev: Depends: libgoogle-perftools0 (= 0.98-1ubuntu1) but it is not installable
Unable to resolve dependencies!  Giving up...
The following packages are BROKEN:
  libgoogle-perftools-dev
0 packages upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 473kB of archives. After unpacking 1499kB will be used.
aptitude failed to find a solution to these dependencies.  You can solve them yourself by hand or type 'n' to quit.
The following packages have unmet dependencies:
  libgoogle-perftools-dev: Depends: libgoogle-perftools0 (= 0.98-1ubuntu1) but it is not installable
Resolve these dependencies by hand? [N/+/-/_/:/?] ^C

```

---

### Post by slattman on 2011-08-30
this is a hack but it will do the trick for now until the repo gets updated.

edit /var/lib/dpkg/status and find libgoogle-perftools0 and change the version to the version its asking for. save and retry.

---

