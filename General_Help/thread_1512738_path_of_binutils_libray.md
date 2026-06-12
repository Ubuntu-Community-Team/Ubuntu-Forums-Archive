---
title: "path of binutils libray"
date: 2010-06-18
forum: General Help
---

### Post by MarD on 2010-06-18
Hallo alle,
wie kann ich den Pfad zum GNU binutils in meinem Ubuntu finden?


Gruss

---

### Post by gzarkadas on 2010-06-18
Open a terminal and use this command to find where binutils files have been installed:
```

cat /var/lib/dpkg/info/binutils.list | less

```If you get an error that the file does not exist, then binutils is not installed. Either do a ```
sudo apt-get install binutils
``` or use menu `System|Administration|Synaptic Package Manager' to open Synaptic and install it through its gui.

In my system the binutils paths are:

Executables:[INDENT]/usr/bin/size
/usr/bin/objdump
/usr/bin/ar
/usr/bin/strings
/usr/bin/ranlib
/usr/bin/objcopy
/usr/bin/addr2line
/usr/bin/readelf
/usr/bin/nm
/usr/bin/strip
/usr/bin/c++filt
/usr/bin/as
/usr/bin/gprof
/usr/bin/ld
[/INDENT]Library files:[INDENT]/usr/lib/libbfd-2.20.so
/usr/lib/libopcodes-2.20.so
/usr/lib/ldscripts/*
[/INDENT]

---

