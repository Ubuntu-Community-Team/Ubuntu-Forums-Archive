---
title: "apt-get does not work"
date: 2010-03-14
forum: General Help
---

### Post by Marwa.Gabbani on 2010-03-14
Hi,
my problem was occur after I compiled my kernel, my old kernel was "2.6.27-17-generic" and the new one is "-2.6.27.18-custom", and when I boot from old one  "2.6.27-17-generic"  and trying to install any package "here i try to install jflex" by using apt-get the following problem shows:

 #apt-get install jflex
Reading package lists... Done
Building dependency tree       
Reading state information... Done
jflex is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 329 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.27.18-custom (2.6.27.18-custom-10.00.Custom) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
gzip: stdout: No space left on device
mkinitramfs-kpkg failed to create initrd image.
Failed to create initrd image.
dpkg: error processing linux-image-2.6.27.18-custom (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 linux-image-2.6.27.18-custom
E: Sub-process /usr/bin/dpkg returned an error code (1)


Can any one help me
:-k, please.

---

### Post by dcstar on 2010-03-14
> **Marwa.Gabbani said:**
> Hi,
my problem was occur after I compiled my kernel, my old kernel was "2.6.27-17-generic" and the new one is "-2.6.27.18-custom", and when I boot from old one  "2.6.27-17-generic"  and trying to install any package "here i try to install jflex" by using apt-get the following problem shows:

 #apt-get install jflex
Reading package lists... Done
Building dependency tree       
Reading state information... Done
jflex is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 329 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.27.18-custom (2.6.27.18-custom-10.00.Custom) ...
Running depmod.
Finding valid ramdisk creators.
Using mkinitramfs-kpkg to build the ramdisk.
**gzip: stdout: No space left on device**
mkinitramfs-kpkg failed to create initrd image.
Failed to create initrd image.
dpkg: error processing linux-image-2.6.27.18-custom (--configure):
 subprocess post-installation script returned error exit status 9
Errors were encountered while processing:
 linux-image-2.6.27.18-custom
E: Sub-process /usr/bin/dpkg returned an error code (1)


Can any one help me
:-k, please.

Find out what has no space left.

---

### Post by Marwa.Gabbani on 2010-03-22
Thanks a lot the problem solved, just I deleted bad packages named linux-image-2.6.27.18-custom  in /var/lib/dpkg/info/ after that I ran 
#apt-get -f install
and then it is work properly :D

---

