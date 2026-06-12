---
title: "problems in installing PHC DKMS package for AMD processors"
date: 2010-05-14
forum: General Help
---

### Post by d2pal on 2010-05-14
I installed "linux-generic-pae-phc" and "linux-headers-generic-pae-phc"  through PPA, and then installed PHC DKMS package by the command "sudo  make dkms_install".
After installation, I checked the directory  "/sys/devices/system/cpu/cpu0/cpufreq/". There are no files starting  with "phc_", so my installation is failed.
How to make it work? Here  are my processes of installation&#65306;

mindforce@mindforce-desktop:~/&#26700; &#38754;/phc$ sudo make dkms_install
[sudo] password for mindforce:
mkdir  -p ""/usr/src/"phc-k8"-"0.4.2"""
install -m 644 -o root -g root  Makefile dkms.conf phc-k8.c phc-k8.h ""/usr/src/"phc-k8"-"0.4.2"""
install  -m 744 -o root -g root phc-k8.add ""/usr/src/"phc-k8"-"0.4.2"""
dkms  add build install -m "phc-k8" -v "0.4.2"

Creating symlink  /var/lib/dkms/phc-k8/0.4.2/source ->
/usr/src/phc-k8-0.4.2

Running  the post_add script:

DKMS: add Completed.

Kernel  preparation unnecessary for this kernel. Skipping...

Building  module:
cleaning build area....
make  KERNELRELEASE=2.6.32-22-generic-pae-phc -C  /lib/modules/2.6.32-22-generic-pae-phc/build  SUBDIRS=/var/lib/dkms/phc-k8/0.4.2/build modules.....
cleaning build  area....

DKMS: build Completed.

phc-k8.ko:
Running  module version sanity check.
- Original module
- No original  module exists within this kernel
- Installation
- Installing to  /lib/modules/2.6.32-22-generic-pae-phc/updates/dkms/

/etc/modprobe.d/phc-k8.conf:  added 'install powernow-k8 /sbin/modprobe phc-k8 || { /sbin/modprobe  --ignore-install powernow-k8; }'
/etc/modprobe.d/phc-k8.conf: added  'remove powernow-k8 /sbin/modprobe -r cpufreq_stats && {  /sbin/modprobe --ignore-remove -r powernow-k8 ; }'
/etc/modprobe.d/phc-k8.conf:  added 'remove phc-k8 /sbin/modprobe -r cpufreq_stats && {  /sbin/modprobe --ignore-remove -r phc-k8 ; }'
depmod......

DKMS:  install Completed.

---

### Post by jjpcexpert on 2010-08-07
With me, it isn't that I cannae get it to install, 's that I cannae use the PHCTool. I need urgent help here:!: 

But, I am in a similar situation to you. I need an underclock.

---

