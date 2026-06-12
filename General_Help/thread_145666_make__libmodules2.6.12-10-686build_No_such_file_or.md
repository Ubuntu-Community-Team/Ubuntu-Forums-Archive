---
title: "make: *** /lib/modules/2.6.12-10-686/build: No such file or directory?"
date: 2006-03-16
forum: General Help
---

### Post by yl200001 on 2006-03-16
I tried to build a VPN netlock software, but below message appeared:
===>
cd src && make all
make[1]: Entering directory `/home/yl200001/cvc_linux-rh-gcc3-3.3/src'
cd k2.6 && make
make[2]: Entering directory `/home/yl200001/cvc_linux-rh-gcc3-3.3/src/k2.6'
make -C /lib/modules/2.6.12-10-686/build SUBDIRS=/home/yl200001/cvc_linux-rh-gcc3-3.3/src/k2.6 modules
make: *** /lib/modules/2.6.12-10-686/build: No such file or directory.  Stop.
make: Entering an unknown directorymake: Leaving an unknown directorymake[2]: *** [kmod_build] Error 2
make[2]: Leaving directory `/home/yl200001/cvc_linux-rh-gcc3-3.3/src/k2.6'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/yl200001/cvc_linux-rh-gcc3-3.3/src'
make: *** [all] Error 2
<===

Why did this happen?

I upgade to new kernel 2.6.12-10 via "apt-get install linux-686".
$uname -r
2.6.12-10-686

pls help.

---

### Post by sublime on 2006-03-16
you need to download the source and headers for your kernel.   go into synaptics and do a search for kernel headers and kernel source and dl the ones specifically fr your kernel version.

---

