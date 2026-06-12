---
title: "FGLRX kernel module failed to built/Ati Graphic card"
date: 2012-06-10
forum: General Help
---

### Post by GreatDanton on 2012-06-10
Hey!
In the previous days I was playing with the Graphic drivers, since when I draw something in gimp 2.8 and then when I want to make floating object, the moving of the floating object was not moving smooth.

Graphic card: Ati Radeon HD 4800 series

Problem:
I downloaded the drivers from Ati site (for linux of course). I followed this site:[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI). The problem occured with this command:sudo dpkg -i *.deb

This is the problem:
```
Selecting previously unselected package fglrx.
(Reading database ... 193194 files and directories currently installed.)
Unpacking fglrx (from fglrx_8.961-0ubuntu1_i386.deb) ...
Selecting previously unselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from fglrx-amdcccle_8.961-0ubuntu1_i386.deb) ...
Selecting previously unselected package fglrx-dev.
Unpacking fglrx-dev (from fglrx-dev_8.961-0ubuntu1_i386.deb) ...
Setting up fglrx (2:8.961-0ubuntu1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group i386-linux-gnu_gl_conf is broken.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl64.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl64.icd (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group i386-linux-gnu_gl_conf) doesn't exist.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.961 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-24-generic-pae
Building for architecture i686
Building initial module for 3.2.0-24-generic-pae
Error! Bad return status for module build on kernel: 3.2.0-24-generic-pae (i686)
Consult /var/lib/dkms/fglrx/8.961/build/make.log for more information.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle (2:8.961-0ubuntu1) ...
Setting up fglrx-dev (2:8.961-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

Crash report is in the attachments.
However I am able to install drivers via System settings/Aditional drivers.
Just to let you know I am trying to change drivers because of Gimp/Maybe after that it will run smooth.

Does anybody know how to solve this. Any help would be appreciated.
Thanks in advance

---

### Post by GreatDanton on 2012-06-14
bump

---

### Post by gAzZa! on 2012-06-17
Bump from me also.  Frustratingly having to go back to Windows 7 at the moment as this is not working properly :mad:

---

### Post by Redblade20XX on 2012-06-17
Follow the instructions here: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

-Red

---

