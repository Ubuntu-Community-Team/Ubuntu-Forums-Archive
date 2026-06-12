---
title: "VMware can't work"
date: 2010-11-25
forum: General Help
---

### Post by didospear on 2010-11-25
Hi

I have installed VMware (VMware-Player-3.0.1-227600.x86_64.bundle) on my laptop. When I open Vmware from Applications/System Tools/VMware Player

I get a window that says: VMware Kernel Module Updater
Before you can run VMware, several modules must be compiled and loaded into the running kernel

When I click on install and after putting in my passwd

a window comes up with a list:
Compiling:
            Virtual Machine Monitor
             Virtual Network Device
             VMware Blocking Filesystem
              Virtual Machine Communication Interface
               VMCI Sockets

But it just try the first one and show an error (window) that says

unable to build kernel module
see log file /tmp/vmware-root/setup-9572.log for details


I cannot even go into the folder vmware-root because it says I do not have permissions even though am an administrator.

How can I get this done or how do I install this thing.

Thanking you in advance.

---

### Post by pawhtiobo on 2010-11-25
Hi :)

Can you do:

$gksudo nautilus

and access the vmware folder?

I say this because it would be nice to see the /tmp/vmware-root/setup-9572.log.


See ya...

---

### Post by didospear on 2010-11-26
Hi

Thanks: this is what the setup-##.log file look like in the /tmp/vmware-root folder: 

Nov 26 10:49:54.732: app-140706459502336| Log for VMware Workstation pid=14057 version=7.0.1 build=build-227600 option=Release
Nov 26 10:49:54.732: app-140706459502336| The process is 64-bit.
Nov 26 10:49:54.732: app-140706459502336| Host codepage=UTF-8 encoding=UTF-8
Nov 26 10:49:54.732: app-140706459502336| Logging to /tmp/vmware-root/setup-14057.log
Nov 26 10:49:54.839: app-140706459502336| modconf query interface initialized
Nov 26 10:49:54.839: app-140706459502336| modconf library initialized
Nov 26 10:49:54.860: app-140706459502336| Your GCC version: 4.4
Nov 26 10:49:54.865: app-140706459502336| Your GCC version: 4.4
Nov 26 10:49:54.871: app-140706459502336| Your GCC version: 4.4
Nov 26 10:49:54.881: app-140706459502336| Your GCC version: 4.4
Nov 26 10:49:54.887: app-140706459502336| Your GCC version: 4.4
Nov 26 10:49:54.912: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:54.913: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:54.915: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:54.917: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:54.919: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:54.930: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:54.932: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:54.934: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:54.936: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:54.937: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:54.940: app-140706459502336| Your GCC version: 4.4
Nov 26 10:49:54.947: app-140706459502336| Your GCC version: 4.4
Nov 26 10:49:54.972: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:54.973: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:54.975: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:54.977: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:54.979: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:54.982: app-140706459502336| Your GCC version: 4.4
Nov 26 10:49:54.989: app-140706459502336| Your GCC version: 4.4
Nov 26 10:49:55.023: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:55.025: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:55.026: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:55.028: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:55.030: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:55.191: app-140706459502336| Trying to find a suitable PBM set for kernel 2.6.35-22-generic.
Nov 26 10:49:55.192: app-140706459502336| Building module vmmon.
Nov 26 10:49:55.192: app-140706459502336| Extracting the sources of the vmmon module.
Nov 26 10:49:55.201: app-140706459502336| Building module with command: /usr/bin/make -C /tmp/vmware-root/modules/vmmon-only auto-build SUPPORT_SMP=1 HEADER_DIR=/lib/modules/2.6.35-22-generic/build/include CC=/usr/bin/gcc GREP=/usr/bin/make IS_GCC_3=no VMCCVER=4.4.5
Nov 26 10:49:57.405: app-140706459502336| Failed to compile module vmmon!

---

### Post by jim_deadlock on 2010-11-26
I would suggest installing virtualbox instead, I've found it to be less problematic than VMware. Don't install it from the repositories though otherwise you'll get the open source version which has its own problems. Go to [http://www.virtualbox.org]("http://www.virtualbox.org/") to get the original version.

---

### Post by didospear on 2010-11-26
Thanks for the responce

There is no virtual box for the kernel I am running (ubuntu 2.6.35-22-generic)... any idea where can I get it?

---

### Post by jim_deadlock on 2010-11-26
I don't think it matters which kernel you have, just choose the download for whichever Ubuntu version you have from this list:

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by dcstar on 2010-11-26
> **didospear said:**
> Hi

I have installed VMware (VMware-Player-3.0.1-227600.x86_64.bundle) on my laptop. When I open Vmware from Applications/System Tools/VMware Player
.........
How can I get this done or how do I install this thing.

Thanking you in advance.

There are threads in the Virtualization forum on installing this.

---

### Post by didospear on 2010-11-26
Hi

dcstar...: where are the threads in the Virtualization for instaling the virtual player.

I have since installed ubuntu 10.10 and I still have no joy. I have downloaded the virtualbox-3.2_3.2.10-66523~Ubuntu~maverick_amd64.deb

I get the following erroe:  Dependency is not satisfiable: libqt4-network (>= 4:4.5.3) 

Any ideas?

Dido

---

### Post by jim_deadlock on 2010-11-26
Try this:

```
sudo apt-get install libqt4-network
```

---

### Post by didospear on 2010-11-29
Jim

Thanx a lot, it worked fine... but I had to manually download "aptitude_0.6.3-2ubuntu4_amd64.deb and install it. else the sudo apt-get install libqt4-network was also giving an error which I did not record and it is now not showing after installing the "aptitude###".

Thanks once more.

Dido

---

