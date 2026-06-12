---
title: "Wine Dependency Problems"
date: 2012-09-12
forum: General Help
---

### Post by freakycheeseman on 2012-09-12
So, I've been messing around with Wine for a few days, trying to get something else working, and completely screwed up. Right now Wine is uninstalled, and when I try to install it (through the software center) I get:
> Package dependencies cannot be resolved
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

wine1.4: PreDepends: dpkg (>= 1.15.7.2~) but 1.16.1.2ubuntu7 is to be installed
         Depends: libc6 (>= 2.14) but 2.15-0ubuntu10 is to be installed
         Depends: wine1.4-amd64 (= 1.4.1-0ubuntu1~precise1~ppa3) but 1.4.1-0ubuntu1~precise1~ppa3 is to be installed
         Depends: wine1.4-i386 (= 1.4.1-0ubuntu1~precise1~ppa3) but it is a virtual package



I've also tried downloading the tarball and trying to install that way. When i do $make, it runs for a while, then ends with

> input.c:913:5: error: ‘union generic_request’ has no member named ‘get_registered_raw_input_devices_request’
input.c:913:5: error: ‘union generic_reply’ has no member named ‘get_registered_raw_input_devices_reply’
input.c:913:1: error: ‘REQ_get_registered_raw_input_devices’ undeclared (first use in this function)
input.c:915:12: error: dereferencing pointer to incomplete type
input.c:921:35: error: dereferencing pointer to incomplete type
input.c:925:27: error: dereferencing pointer to incomplete type
make[1]: *** [input.o] Error 1
make[1]: Leaving directory `/var/wine/wine-1.4/dlls/user32'
make: *** [dlls/user32] Error 2


Any idea how to fix this?

---

### Post by dozdozez on 2012-09-12
I would try to refresh the package list and upgrade everything

using synaptic: reload , and then mark all upgrades, mark wine to install,  aply.

or usig apt-get:
```

apt-get update
apt-get upgrade
apt-get install wine 
```

---

### Post by freakycheeseman on 2012-09-12
Huh. I tried the terminal one, and got

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine is already the newest version.
wine set to manually installed.
The following packages were automatically installed and are no longer required:
  libunity6 wine-gecko1.4:i386
Use 'apt-get autoremove' to remove them.


But wine won't launch, and the software center doesn't think it's installed.

---

### Post by freakycheeseman on 2012-09-12
Nevermind, I got it working. Did basically what you said with synaptic, but had to food around a bit, mark assorted things for complete removal.

---

