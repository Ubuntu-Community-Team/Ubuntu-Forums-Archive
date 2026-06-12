---
title: "Graphics installation issues"
date: 2012-07-03
forum: General Help
---

### Post by andizam on 2012-07-03
Hello,
When installing my FGLRX-updates driver, I get the following errors and I have no idea what they mean. Jockey-text in terminal always fails to enable it, and I used "dpkg --force-all" in terminal to no avail

```
sudo dpkg --force-all -i fglrx-updates_8.960-0ubuntu1_i386.deb fglrx-amdcccle-updates_8.960-0ubuntu1_i386.deb
Selecting previously unselected package fglrx-updates.
(Reading database ... 172527 files and directories currently installed.)
Unpacking fglrx-updates (from fglrx-updates_8.960-0ubuntu1_i386.deb) ...
Selecting previously unselected package fglrx-amdcccle-updates.
Unpacking fglrx-amdcccle-updates (from fglrx-amdcccle-updates_8.960-0ubuntu1_i386.deb) ...
Setting up fglrx-updates (2:8.960-0ubuntu1) ...

Configuration file `/etc/init.d/atieventsd', does not exist on system.
Installing new config file as you requested.

Configuration file `/etc/acpi/events/fglrx-ac-aticonfig', does not exist on system.
Installing new config file as you requested.

Configuration file `/etc/acpi/events/fglrx-lid-aticonfig', does not exist on system.
Installing new config file as you requested.

Configuration file `/etc/acpi/fglrx-powermode.sh', does not exist on system.
Installing new config file as you requested.
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
Loading new fglrx-updates-8.960 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-26-generic-pae
Building for architecture i686
Building initial module for 3.2.0-26-generic-pae
Done.

fglrx_updates:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-26-generic-pae/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for ureadahead ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle-updates (2:8.960-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic-pae
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by dino99 on 2012-07-03
i suppose its working: " install completed." right ?

but why are you following this scary way ? is default ubuntu driver choice not good for you ?

---

### Post by andizam on 2012-07-03
No, it doesn't say install completed, it just goes back to the normal directory. I can't use the driver installer because it always fails to install, just like the using jockey-text in terminal.

---

### Post by QIII on 2012-07-03
What is the model of card you are using?  We need to know if it is supported.

Please give the wiki link in my signature a look.

Some users are reporting difficulty with fglrx-updates and fglrx-amdcccle-updates, as well as using jockey.

I added a section about using an alternate command line method that includes activation of hardware acceleration.

---

### Post by andizam on 2012-07-03
Thank you. It's a Mobility Radeon HD 4250, so apparently it works. I'll give the command-line method a try and come back with my results!

---

### Post by andizam on 2012-07-03
So I gave the command-line method a try. It installed well, I enabled 3D acceleration as it said in the guide and in catalyst control center, but still I can only login to Ubuntu 2D. Ubuntu desktop loads the launcher, but totally unresponsive to my mouse. Even Gnome classic won't load anything at all. I have no idea what the problem could possibly be.

---

