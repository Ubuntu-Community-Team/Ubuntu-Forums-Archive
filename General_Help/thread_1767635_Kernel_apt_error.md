---
title: "Kernel apt error?"
date: 2011-05-25
forum: General Help
---

### Post by BrandonC19 on 2011-05-25
Anyone know what to do about this? 
```
root@brandon-laptop:/home/brandon# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.35-29-generic (2.6.35-29.51) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-29-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-29-generic /boot/vmlinuz-2.6.35-29-generic
 * dkms: running auto installation service for kernel 2.6.35-29-generic         
 *       vboxhost (4.0.6)...                                             [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-29-generic /boot/vmlinuz-2.6.35-29-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-29-generic /boot/vmlinuz-2.6.35-29-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-29-generic /boot/vmlinuz-2.6.35-29-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-29-generic /boot/vmlinuz-2.6.35-29-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-29-generic /boot/vmlinuz-2.6.35-29-generic
Generating grub.cfg ...
Found background image: CCRBokeh.tga
/etc/grub.d/05_debian_theme.save: 27: Syntax error: "then" unexpected (expecting "do")
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-29-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-29-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-29-generic; however:
  Package linux-image-2.6.35-29-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.29.37); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfiNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                No apport report written because the error message indicates its a followup error from a previous failure.
          gured
Errors were encountered while processing:
 linux-image-2.6.35-29-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
After trying to install Torcs I got these errors, and they show up again after an ```
apt-get install -f
```
Feel free to gimme your best shot I'm pretty fluent in CLI-speak. ;)

---

### Post by BrandonC19 on 2011-05-26
Bump...heh heh...
 :popcorn:

---

### Post by BrandonC19 on 2011-05-26
Actually, never mind. I figured it out myself. I fixed everything by deleting the contents of /var/lib/dpkg/info and /var/cache/apt/archives. Marking as solved.

---

