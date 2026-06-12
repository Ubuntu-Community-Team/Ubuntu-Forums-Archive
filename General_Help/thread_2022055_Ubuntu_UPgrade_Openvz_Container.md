---
title: "Ubuntu UPgrade Openvz Container"
date: 2012-07-10
forum: General Help
---

### Post by gineta on 2012-07-10
Hi I make many upgrades in my OPenvz container with Ubuntu but when I upgrade to Ubuntu 12 I got many problems with the grub loader and the kernel 

if I make a simple task like install a php package with aptitude
I got always 

The following partially installed packages will be configured:
  linux-generic linux-generic-pae linux-image-2.6.38-15-generic linux-image-2.6.38-15-generic-pae linux-image-2.6.38-8-virtual linux-image-generic 
  linux-image-generic-pae linux-image-server linux-server 

if I continuous I install what I need but I get a big list of error at the end with all that missing kernels
ANY ideas please how to solve all the problem Thanks in advance

> Setting up linux-image-2.6.38-15-generic (2.6.38-15.61) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-15-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-15-generic /boot/vmlinuz-2.6.38-15-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-15-generic /boot/vmlinuz-2.6.38-15-generic
/usr/sbin/grub-probe: error: cannot stat `/var/lib/vz/private/107'.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-15-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-2.6.38-15-generic-pae (2.6.38-15.61) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-15-generic-pae
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-15-generic-pae /boot/vmlinuz-2.6.38-15-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-15-generic-pae /boot/vmlinuz-2.6.38-15-generic-pae
/usr/sbin/grub-probe: error: cannot stat `/var/lib/vz/private/107'.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-15-generic-pae.postinst line 1010.
dpkg: error processing linux-image-2.6.38-15-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-2.6.38-8-virtual (2.6.38-8.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-8-virtual
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-8-virtual /boot/vmlinuz-2.6.38-8-virtual
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-8-virtual /boot/vmlinuz-2.6.38-8-virtual
/usr/sbin/grub-probe: error: cannot stat `/var/lib/vz/private/107'.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-8-virtual.postinst line 1010.
dpkg: error processing linux-image-2.6.38-8-virtual (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-15-generic; however:
  Package linux-image-2.6.38-15-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.15.30); however:
  Package linux-image-generic is not configured yet.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.38-15-generic-pae; however:
  Package linux-image-2.6.38-15-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.38.15.30); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-generic-pae; however:
  Package linux-image-generic-pae is not configured yet.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-generic-pae; however:
  Package linux-generic-pae is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.38-15-generic
 linux-image-2.6.38-15-generic-pae
 linux-image-2.6.38-8-virtual
 linux-image-generic
 linux-generic
 linux-image-generic-pae
 linux-generic-pae
 linux-image-server
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.38-15-generic-pae (2.6.38-15.61) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-15-generic-pae
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-15-generic-pae /boot/vmlinuz-2.6.38-15-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-15-generic-pae /boot/vmlinuz-2.6.38-15-generic-pae
/usr/sbin/grub-probe: error: cannot stat `/var/lib/vz/private/107'.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-15-generic-pae.postinst line 1010.
dpkg: error processing linux-image-2.6.38-15-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.38-8-virtual (2.6.38-8.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-8-virtual
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-8-virtual /boot/vmlinuz-2.6.38-8-virtual
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-8-virtual /boot/vmlinuz-2.6.38-8-virtual
/usr/sbin/grub-probe: error: cannot stat `/var/lib/vz/private/107'.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-8-virtual.postinst line 1010.
dpkg: error processing linux-image-2.6.38-8-virtual (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.38-15-generic (2.6.38-15.61) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-15-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-15-generic /boot/vmlinuz-2.6.38-15-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-15-generic /boot/vmlinuz-2.6.38-15-generic
/usr/sbin/grub-probe: error: cannot stat `/var/lib/vz/private/107'.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-15-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.38-15-generic-pae; however:
  Package linux-image-2.6.38-15-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-15-generic; however:
  Package linux-image-2.6.38-15-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.38.15.30); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-generic-pae; however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-generic-pae; however:
  Package linux-generic-pae is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.15.30); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.38-15-generic-pae
 linux-image-2.6.38-8-virtual
 linux-image-2.6.38-15-generic
 linux-image-generic-pae
 linux-image-generic
 linux-generic-pae
 linux-image-server
 linux-server
 linux-generic


---

