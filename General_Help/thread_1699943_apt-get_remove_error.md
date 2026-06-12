---
title: "apt-get remove error"
date: 2011-03-04
forum: General Help
---

### Post by shade34321 on 2011-03-04
I have my hard drive partitioned so my /boot has 60 mb. Recently I tried to update and I got an error saying my /boot is full. Below is what I get when I type in apt-get remove. I also noticed that when I run apt-get update it asks me for the Ubuntu 10.10 server CD. Thanks in advance! 



shade@Reptar:~$ sudo apt-get remove
[sudo] password for shade: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjna-java libswing-layout-java javahelp2 libfelix-main-java visualvm
  libfelix-framework-java libnb-platform12-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up initramfs-tools (0.98.1ubuntu6) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-2.6.35-27-generic (2.6.35-27.48) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-27-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-2.6.35-27-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-27-generic; however:
  Package linux-image-2.6.35-27-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.27.35); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-2.6.35-25-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.35-27-generic
 linux-image-generic
 linux-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by turtle153 on 2011-03-04
You're probably out of space in /boot. Mine takes up 133MB so 60 is noway enough.

You might be asked for the CD if its enabled in Software Sources. Open up Update Manager and click Settings. Under the Other Software tab, deselect "CD-ROM with Ubuntu"

---

### Post by shade34321 on 2011-03-04
I'm under the impression the only thing that's really in /boot are the kernel files and since I did a fresh install of ubuntu 10.10 on this laptop not even two months ago there really shouldn't be many/any newer kernels. I'm also under the impression that this kernel files aren't very big(just googling /boot full brought up a host of websites). I could be wrong and try and make /boot bigger but I'm not sure if that's the main reason. You're advice for the CD worked like a charm thanks:)

---

### Post by turtle153 on 2011-03-04
Good that that worked :) Just right click /boot in file manager and look at the properties. I would never put caps on critical folders because you never know what might happen if a file there can't be written to if there's no space.

---

