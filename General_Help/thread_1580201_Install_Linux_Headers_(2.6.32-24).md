---
title: "Install Linux Headers (2.6.32-24)?"
date: 2010-09-23
forum: General Help
---

### Post by GrantStoner on 2010-09-23
How do you install headers? Is it different for every version? Synaptic seems to have them all except for my kernel! When I do a ```
ls /boot
```it returns with ```
abi-2.6.32-24-generic	      memtest86+.bin
config-2.6.32-24-generic      System.map-2.6.32-24-generic
grub			      vmcoreinfo-2.6.32-24-generic
initrd.img-2.6.32-24-generic  vmlinuz-2.6.32-24-generic
```
I tried to install them with ```
sudo apt-get install linux-headers-$(uname -r)
```
Here is what I've tried and here's the results:```
grant@TheHaxLab:~$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.32-24-generic
grant@TheHaxLab:~$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
The following NEW packages will be installed:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
  linux-headers-generic
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.6MB of archives.
After this operation, 85.3MB of additional disk space will be used.
Do you want to continue [Y/n]? ^C
grant@TheHaxLab:~$
```
What is going on? I have the kernel for 2.6.32-24, but it can't find the headers for it? Why is it choosing and trying to install the headers for 2.6.32-21?

Oh, and do I need linux-headers-generic AND linux-headers-2.6.32-24 AND linux-headers-2.6.32-24-generic? Or if I do one, will it automatically install them all?

---

### Post by andrewthomas on 2010-09-23
[linux-headers-2.6.32-24   ]("http://packages.ubuntu.com/lucid/linux-headers-2.6.32-24")Header files related to Linux kernel version 2.6.32
[linux-headers-2.6.32-24-386   ]("http://packages.ubuntu.com/lucid/linux-headers-2.6.32-24-386")Linux kernel headers for version 2.6.32 on i386
[linux-headers-2.6.32-24-generic   ]("http://packages.ubuntu.com/lucid/linux-headers-2.6.32-24-generic")Linux kernel headers for version 2.6.32 on x86/x86_64
[linux-headers-2.6.32-24-generic-pae]("http://packages.ubuntu.com/lucid/linux-headers-2.6.32-24-generic-pae")   Linux kernel headers for version 2.6.32 on x86
[linux-headers-2.6.32-24-preempt]("http://packages.ubuntu.com/lucid/linux-headers-2.6.32-24-preempt")   Linux kernel headers for version 2.6.32 on x86_64
[linux-headers-2.6.32-24-server]("http://packages.ubuntu.com/lucid/linux-headers-2.6.32-24-server")  Linux kernel headers for version 2.6.32 on x86_64

[http://packages.ubuntu.com/lucid/linux-headers](http://packages.ubuntu.com/lucid/linux-headers)

and yes the linux-headers-generic is a metapackage. This package will always depend on the latest generic kernel headers available.

---

### Post by efflandt on 2010-09-23
See what headers you have in /usr/src, they should be there automatically from kernel updates.  I removed earlier Linux version(s) with Synaptic and g13-userspace is something I compiled for a gamepad:

```
ls -l /usr/src
total 24
drwxr-xr-x  2 efflandt efflandt 4096 2010-09-22 03:39 g13-userspace
drwxr-xr-x 24 root     root     4096 2010-07-08 23:51 linux-headers-2.6.32-23
drwxr-xr-x  7 root     root     4096 2010-07-08 23:51 linux-headers-2.6.32-23-generic
drwxr-xr-x 24 root     root     4096 2010-09-18 12:08 linux-headers-2.6.32-24
drwxr-xr-x  7 root     root     4096 2010-09-18 12:09 linux-headers-2.6.32-24-generic
drwxr-xr-x  3 root     root     4096 2010-07-12 22:47 nvidia-current-195.36.24
```

---

### Post by GrantStoner on 2010-09-23
Here's what it gave me.
```
grant@TheHaxLab:~$ ls -l /usr/src
total 4
drwxr-xr-x 12 root root 4096 2010-08-11 01:49 virtualbox-ose-3.1.6
grant@TheHaxLab:~$ 


```

Looks like there's nothing in there from any headers? Except for what's in my virtualbox.

---

