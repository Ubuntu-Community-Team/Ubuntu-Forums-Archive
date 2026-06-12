---
title: "Unable to upgrade kernel in 9.04"
date: 2009-07-10
forum: General Help
---

### Post by gritsisgood on 2009-07-10
One of my 9.04 installs is having problems upgrading the kernel. Every time I try to install the latest kernel, I get an error message about an exit status of 116 from the post-installation script. In addition, Nautilus has stopped displaying icons for the "File System" location - only "lost+found" shows up. Attempting to list files in the root filesystem from a terminal shows the following message:

$ ls
ls: cannot access cdrom: Input/output error
ls: cannot access vmlinuz: Stale NFS file handle
ls: cannot access vmlinuz.old: Stale NFS file handle
ls: cannot access initrd.img.old: Stale NFS file handle
ls: cannot access initrd.img: Stale NFS file handle
bin    dev   initrd.img      lost+found  opt   sbin     sys  var
boot   etc   initrd.img.old  media       proc  selinux  tmp  vmlinuz
cdrom  home  lib             mnt         root  srv      usr  vmlinuz.old

The message that appears in the terminal output for the upgrade is:
Setting up linux-image-2.6.28-13-generic (2.6.28-13.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-13-generic
Failed to symbolic-link boot/initrd.img-2.6.28-13-generic to initrd.img.
dpkg: error processing linux-image-2.6.28-13-generic (--configure):
 subprocess post-installation script returned error exit status 116
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-13-generic; however:
  Package linux-image-2.6.28-13-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.28.13.17); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured

Errors were encountered while processing:
 linux-image-2.6.28-13-generic
 linux-image-generic
 linux-image
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.28-13-generic (2.6.28-13.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-13-generic
Failed to symbolic-link boot/initrd.img-2.6.28-13-generic to initrd.img.
dpkg: error processing linux-image-2.6.28-13-generic (--configure):
 subprocess post-installation script returned error exit status 116
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-13-generic; however:
  Package linux-image-2.6.28-13-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.28.13.17); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.28-13-generic
 linux-image-generic
 linux-image

Attached also is a screenshot of the Nautilus display of the "File System" location.

Any ideas?
Thanks!

---

### Post by miklcct on 2009-07-13
Your NFS is down.

---

### Post by gritsisgood on 2009-07-13
> **miklcct said:**
> Your NFS is down.
Thanks for the response - I appreciate it. Unfortunately, I'm not running any NFS. The drive that it's speaking of is the second hard drive in a two drive machine. Nothing mounts to this machine remotely. My thought on that particular error notation (Stale NFS mount) is that it must be a canned error message that it uses for a range of symptons related to failure to access a drive. Just a guess.....

Thanks again....

---

