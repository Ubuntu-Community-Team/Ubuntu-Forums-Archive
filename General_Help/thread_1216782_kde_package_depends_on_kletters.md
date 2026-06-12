---
title: "kde package depends on kletters?"
date: 2009-07-18
forum: General Help
---

### Post by HotForLinux on 2009-07-18
I'd like to remove the package **kletters** from a desktop with ubuntu and kde-desktop but.....
I need to remove all **kde**????

No thanks!!

---

### Post by HotForLinux on 2009-07-22
Nobody knows if I can remove kletters without removing all kde. It just doesn't sound normal to me

---

### Post by HotForLinux on 2011-06-16
- Bump -

---

### Post by FormatSeize on 2011-06-16
You won't have to remove an entire desktop environment because of a single, rather insignificant, package. A package about teaching kids the alphabet having dependencies far-reaching enough such that an entire desktop environment has to go if it is removed would be a monumental development failure.
 
What's giving you this idea?

---

### Post by HotForLinux on 2011-06-16
> **FormatSeize said:**
> ... What's giving you this idea?... 

I cannot remember but I think that, after a year, the dependencies have changed a lot, and now less packages need to be removed, but still the dependencies are strong and it seems strange that I need to remove several packages:


```
Package: klettres
State: installed
Automatically installed: yes
Version: 4:3.5.10-0ubuntu1~hardy1
Priority: optional
Section: kde
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1069k
Depends: kdeedu-data (> 4:3.5.10), kdeedu-data (< 4:3.5.11), kdelibs4c2a (>= 4:3.5.8-1), klettres-data (>
         4:3.5.10), klettres-data (< 4:3.5.11), libc6 (>= 2.4), libgcc1, libqt3-mt (>= 3:3.3.8-b), libstdc++6
         (>= 4.1.1-21)
```

```
aptitude -s remove  klettres
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  kdeedu 
The following packages have been kept back:
  libxml2 libxml2-dev libxml2-utils python-libxml2 
The following packages will be REMOVED:
  klettres 
0 packages upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 1069kB will be freed.
The following packages have unmet dependencies:
  kdeedu: Depends: klettres (>= 4:3.5.10-0ubuntu1~hardy1) but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
kde
kde-amusements
kdeedu

Score is 257

Accept this solution? [Y/n/q/?]

```

---

