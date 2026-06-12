---
title: "openoffice menu installation"
date: 2011-09-11
forum: General Help
---

### Post by NattyNoobCake on 2011-09-11
im trying to install openofffice 3.3 on natty narwhal (64 bit). I got most of the stuff installed. aka, i can go into the opt directory and run the program via terminal. However, i can't seem to get the "suse menu" and icons installed. The oo website says i should run this code:

```
rpm -Uvh openoffice.org-<dist>-menus-<release>.noarch.rpm
```

where dist is redhat/suse/etc. and release is 3.0, 3.3, etc.

but i simply get this error

> rpm: RPM should not be used directly install RPM packages, use Alien instead!
rpm: However assuming you know what you are doing...
error: Failed dependencies:
	/bin/sh is needed by openoffice.org3.3-freedesktop-menus-3.3-9556.noarch


how can i install the menus?

---

