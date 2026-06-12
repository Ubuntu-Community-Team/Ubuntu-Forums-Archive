---
title: "Error upgrading kernel"
date: 2011-03-04
forum: General Help
---

### Post by Bllz on 2011-03-04
Hello,

When running sudo apt-get upgrade, the following error occurs. 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.35-28-generic (2.6.35-28.49) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-28-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
 * dkms: running auto installation service for kernel 2.6.35-28-generic         
 *       nvidia-current (270.29)...                                      [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-28-generic /boot/vmlinuz-2.6.35-28-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-28-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-28-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-28-generic; however:
  Package linux-image-2.6.35-28-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.28.36); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-2.6.35-28-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any suggestions?

Thanks,
Bllz

---

### Post by plucky on 2011-03-04
> /etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2


That might be significant

What does ```
sudo update-grub
``` in a terminal show you?

Good luck

---

