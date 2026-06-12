---
title: "Kubuntu 10.10 upgrade to 11.04, kernel 2.6.38-8 install fails"
date: 2011-05-02
forum: General Help
---

### Post by at165db on 2011-05-02
I started the upgrade procedure on my work computer Thursday.  Today is my 1st day back in the office, and I noticed that the upgrade failed.

The error was about how it could not install the kernel package.  Fun!

It looks like all my apt sources are now pointed to 11.04.

I'm attaching the contents of my /var/log/dist-upgrade.

If I try and reinstall the kernel, I get the following error:
```
russlewi@russlewi-desktop:/var/log/dist-upgrade$ sudo aptitude reinstall linux-image-2.6.38-8-generic
The following packages will be REINSTALLED:
  linux-image-2.6.38-8-generic 
The following partially installed packages will be configured:
  initramfs-tools linux-generic linux-image-generic 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Setting up initramfs-tools (0.98.8ubuntu3) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-2.6.38-8-generic (2.6.38-8.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-2.6.38-8-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.38-8-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-8-generic; however:
  Package linux-image-2.6.38-8-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.8.22); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                        update-initramfs: Generating /boot/initrd.img-2.6.35-29-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-2.6.35-29-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.38-8-generic
 linux-image-generic
 linux-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up initramfs-tools (0.98.8ubuntu3) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-2.6.38-8-generic (2.6.38-8.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic

gzip: stdout: No space left on device
cpio: write error: Broken pipe
E: mkinitramfs failure cpio 1 gzip 1
update-initramfs: failed for /boot/initrd.img-2.6.38-8-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.38-8-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-8-generic; however:
  Package linux-image-2.6.38-8-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.8.22); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-29-generic

gzip: stdout: No space left on device
cpio: write error: Broken pipe
E: mkinitramfs failure cpio 1 gzip 1
update-initramfs: failed for /boot/initrd.img-2.6.35-29-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.38-8-generic
 linux-image-generic
 linux-generic
 initramfs-tools
                  
```

I'm not sure what to do next.  Obviously I'm not going to reboot!

---

### Post by at165db on 2011-05-02
My /boot was full. It looks like the kernel packages fill boot, but never delete old kernels. I'm not sure if there was a "better" way, but I deleted some older images.

Filesystem Size Used Avail Use% Mounted on
 /dev/md1 46G 25G 20G 56% /
 none 3.9G 340K 3.9G 1% /dev
 none 4.0G 2.3M 4.0G 1% /dev/shm
 none 4.0G 276K 4.0G 1% /var/run
 none 4.0G 0 4.0G 0% /var/lock
 /dev/md0 183M 169M 4.4M 98% /boot
 /dev/md2 409G 120G 269G 31% /home

How do I know if there are any other packages to re-install after the kernel to finish the upgrade?

---

