---
title: "Unpacking linux-headers-3.2.0-24 hangs"
date: 2012-05-24
forum: General Help
---

### Post by RussoJustin1976 on 2012-05-24
uname -r
3.2.0-24-generic-pae

sudo apt-get install linux-headers-generic-pae

It hangs at Unpacking linux-headers-3.2.0-24 (from .../linux-headers-3.2.0-24_3.2.0-24.39_all.deb) ...

I forced uninstall with dpkg, apt-get clean, redownloaded and installed again. It always hangs at this point forever. Also hangs on another system.

How can I solve it? I haven't found anything on Google.

---

### Post by cmont899 on 2012-05-24
if you wget the .deb and try to install with dpkg does it complete successfully?

```
dpkg -i <package>.deb
```

---

### Post by RussoJustin1976 on 2012-05-24
No.

dpkg -i linux-headers-3.2.0-24_3.2.0-24.39_all.deb 
```

(Reading database ... 
dpkg: warning: files list file for package `linux-headers-3.2.0-24' missing, assuming package has no files currently installed.
(Reading database ... 61885 files and directories currently installed.)
Preparing to replace linux-headers-3.2.0-24 3.2.0-24.39 (using linux-headers-3.2.0-24_3.2.0-24.39_all.deb) ...
Unpacking replacement linux-headers-3.2.0-24 ...

```dpkg looks being stuck in a loop (runs forever).

dpkg --debug=3773 -i linux-headers-3.2.0-24_3.2.0-24.39_all.deb
```

D000100: setupvnamevbs main=`/usr/src/linux-headers-3.2.0-24/arch/arm/mach-ep93xx/include/mach/platform.h' tmp=`/usr/src/linux-headers-3.2.0-24/arch/arm/mach-ep93xx/include/mach/platform.h.dpkg-tmp' new=`/usr/src/linux-headers-3.2.0-24/arch/arm/mach-ep93xx/include/mach/platform.h.dpkg-new'
D000100: deferred extract needs fsync
D000100: deferred extract needs rename
D000100: deferred extract done and installed
D000010: deferred extract of '/usr/src/linux-headers-3.2.0-24/arch/arm/mach-ep93xx/include/mach/system.h'
D000100: setupvnamevbs main=`/usr/src/linux-headers-3.2.0-24/arch/arm/mach-ep93xx/include/mach/system.h' tmp=`/usr/src/linux-headers-3.2.0-24/arch/arm/mach-ep93xx/include/mach/system.h.dpkg-tmp' new=`/usr/src/linux-headers-3.2.0-24/arch/arm/mach-ep93xx/include/mach/system.h.dpkg-new'
D000100: deferred extract needs fsync
D000100: deferred extract needs rename
D000100: deferred extract done and installed
D000010: deferred extract of '/usr/src/linux-headers-3.2.0-24/arch/arm/mach-ep93xx/include/mach/timex.h'
D000100: setupvnamevbs main=`/usr/src/linux-headers-3.2.0-24/arch/arm/mach-ep93xx/include/mach/timex.h' tmp=`/usr/src/linux-headers-3.2.0-24/arch/arm/mach-ep93xx/include/mach/timex.h.dpkg-tmp' new=`/usr/src/linux-headers-3.2.0-24/arch/arm/mach-ep93xx/include/mach/timex.h.dpkg-new'
D000100: deferred extract needs fsync

```

---

### Post by RussoJustin1976 on 2012-05-28
Anyone?

---

### Post by cmont899 on 2012-05-30
Try clearing your apt ache and updating again:

```
sudo apt-get clean all
sudo apt-get update
sudo apt-get install linux-headers-generic-pae
```

---

### Post by RussoJustin1976 on 2012-05-30
That worked. Thanks!

---

