---
title: "E: Internal Error, No file name for libpng12-0"
date: 2012-02-17
forum: General Help
---

### Post by syntr on 2012-02-17
Hello:

I'm dealing with a problem here that has made it impossible for me to use libpng. I attempted to install the GIMP APNG patch as described here: [http://registry.gimp.org/node/24394](http://registry.gimp.org/node/24394) , which required me to install a patched libpng. I made a mistake during installation and it corrupted my libpng12-0 package. Consequently, I can no longer compile software that relies on libpng12-0.

When I try to reinstall libpng12-0:
```
sudo apt-get install --reinstall --purge libpng12-0
```I get:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 44 not upgraded.
Need to get 0 B/132 kB of archives.
After this operation, 0 B of additional disk space will be used.
**E: Internal Error, No file name for libpng12-0**

```

I've attempted to move the libpng12-0 related files in /var/lib/dpkg/info, but this did not solve the problem.

Here's libpng12-0:amd64.list:
```
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/libpng12-0
/usr/share/doc/libpng12-0/README.gz
/usr/share/doc/libpng12-0/TODO
/usr/share/doc/libpng12-0/ANNOUNCE
/usr/share/doc/libpng12-0/KNOWNBUG
/usr/share/doc/libpng12-0/README.Debian
/usr/share/doc/libpng12-0/copyright
/usr/share/doc/libpng12-0/changelog.Debian.gz
/usr/share/doc/libpng12-0/libpng-1.2.46.txt.gz
/usr/share/doc-base
/usr/share/doc-base/libpng12
/lib
/lib/x86_64-linux-gnu
/lib/x86_64-linux-gnu/libpng12.so.0.46.0
/lib/x86_64-linux-gnu/libpng12.so.0

```

I have no idea what to do. How can I force apt to reinstall this package?

---

### Post by syntr on 2012-02-17
Bump. Haven't made any further headway on this...

---

