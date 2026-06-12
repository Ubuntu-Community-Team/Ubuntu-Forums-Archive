---
title: "Installing gcc-4.3 on 11.10"
date: 2011-10-17
forum: General Help
---

### Post by ErlendA on 2011-10-17
Hi

On ubuntu 11.04 it was straightforward to install gcc-4.3, using meerkats deb-packages ([http://packages.ubuntu.com/maverick/gcc-4.3](http://packages.ubuntu.com/maverick/gcc-4.3)). On 11.10, however, it is problematic: the following dependency breakage occurs:

```

Unpacking gcc-4.3 (from gcc-4.3_4.3.5-3ubuntu1_amd64.deb) ...
dpkg: dependency problems prevent configuration of gcc-4.3:
 libgcc1:i386 (1:4.6.1-9ubuntu3) breaks gcc-4.3 and is installed.
 libgcc1 (1:4.6.1-9ubuntu3) breaks gcc-4.3 and is installed.
dpkg: error processing gcc-4.3 (--install):
 dependency problems - leaving unconfigured

```

For people like me, requiring gcc-4.3 to wrap code into MATLAB, for instance, this is a problem. I need gcc-4.3 to compile code which can run on the computing servers.

Does anybody know another gcc-4.3 package that works or a fix to this?

EDIT: I also tried the ones found here ([http://packages.debian.org/stable/devel/gcc-4.3](http://packages.debian.org/stable/devel/gcc-4.3)) with no success.

---

