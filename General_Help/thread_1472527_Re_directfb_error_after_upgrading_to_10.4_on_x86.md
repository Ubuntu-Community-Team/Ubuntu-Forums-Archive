---
title: "Re: directfb error after upgrading to 10.4 on x86"
date: 2010-05-04
forum: General Help
---

### Post by ma1kel on 2010-05-04
Trying to load some apps like dosbox and virtualbox I get the following error:

```
maikel@computer-maikel:~$ virtualbox
VirtualBox: supR3HardenedMainGetTrustedMain: dlopen("/usr/lib/virtualbox/VirtualBox.so",) failed: libdirectfb-1.0.so.0: cannot open shared object file: No such file or directory
maikel@computer-maikel:~$ sudo virtualbox
VirtualBox: supR3HardenedMainGetTrustedMain: dlopen("/usr/lib/virtualbox/VirtualBox.so",) failed: libdirectfb-1.0.so.0: cannot open shared object file: No such file or directory
maikel@computer-maikel:~$ dosbox
dosbox: error while loading shared libraries: libdirectfb-1.0.so.0: cannot open shared object file: No such file or directory
```

---

### Post by ma1kel on 2010-05-05
bump

---

### Post by dino99 on 2010-05-05
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

