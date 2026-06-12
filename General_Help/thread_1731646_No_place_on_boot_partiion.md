---
title: "No place on boot partiion"
date: 2011-04-17
forum: General Help
---

### Post by hej.mich on 2011-04-17
Hi,
When I try to install anything via apt-get i get 

> You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-generic-pae : Depends: linux-image-2.6.35-28-generic-pae but it is not installed
E: Unmet dependencies. Try using -f.


However on apt-get -f install i get this:

>  sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-23-generic-pae linux-headers-2.6.35-22
  linux-headers-2.6.35-23 linux-headers-2.6.35-24 linux-headers-2.6.35-25
  linux-headers-2.6.35-24-generic-pae linux-headers-2.6.35-25-generic-pae
  linux-headers-2.6.35-22-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-2.6.35-28-generic-pae
Suggested packages:
  fdutils linux-doc-2.6.35 linux-source-2.6.35 linux-tools
The following NEW packages will be installed:
  linux-image-2.6.35-28-generic-pae
0 upgraded, 1 newly installed, 0 to remove and 26 not upgraded.
5 not fully installed or removed.
Need to get 34.1MB of archives.
After this operation, 108MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://pl.archive.ubuntu.com/ubuntu/](http://pl.archive.ubuntu.com/ubuntu/) maverick-updates/main linux-image-2.6.35-28-generic-pae i386 2.6.35-28.50 [34.1MB]
Fetched 34.1MB in 36s (944kB/s)
(Reading database ... 190256 files and directories currently installed.)
Unpacking linux-image-2.6.35-28-generic-pae (from .../linux-image-2.6.35-28-generic-pae_2.6.35-28.50_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.35-28-generic-pae_2.6.35-28.50_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-2.6.35-28-generic-pae': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-28-generic-pae /boot/vmlinuz-2.6.35-28-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-28-generic-pae /boot/vmlinuz-2.6.35-28-generic-pae
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.35-28-generic-pae_2.6.35-28.50_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I've tried autoclean, autoremove etc. I cannot delete old kernels via apt-get either.

> >df
/dev/md0                 93207     92999         0 100% /boot


What I can do in this situation? I can't use gparted because ubuntu uses software raid...

Ubuntu 10.11 Server x86

---

### Post by SeijiSensei on 2011-04-17
That's way too small for /boot; I've found 256M is a good minimum.

That said, you may have a collection of older kernels and associated files that you can remove.  Delete all the files associated with kernels before the last good one you're running.  You may want to delete the appropriate stanzas in /boot/grub/grub.cfg as well.  You'll need to make that file writable before you can edit it, then remove the write permission when you're done.

---

