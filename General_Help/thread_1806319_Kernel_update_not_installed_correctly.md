---
title: "Kernel update not installed correctly"
date: 2011-07-17
forum: General Help
---

### Post by daftlad on 2011-07-17
After doing software updates my system had to be rebooted after a kernel update, but when I checked in grub and using  $ uname -r it reported that I was using 2.6.38-8-generic. Now ever time I install a program from the software centre it says that software can not be installed and gives me these details. I am using Ubuntu 11.04 in unity
Here are the details from the software centre, thanks in advance for any help


installArchives() failed: Selecting previously deselected package linux-image-2.6.38-10-generic. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 183028 files and directories currently installed.) 
Preparing to replace linux-image-2.6.38-10-generic 2.6.38-10.46 (using .../linux-image-2.6.38-10-generic_2.6.38-10.46_i386.deb) ... 
Done. 
Unpacking replacement linux-image-2.6.38-10-generic ... 
Examining /etc/kernel/postrm.d . 
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic 
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic 
Selecting previously deselected package lshw-gtk. 
Unpacking lshw-gtk (from .../lshw-gtk_02.15-1_i386.deb) ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_GB.UTF8.cache... 
Processing triggers for man-db ... 
Processing triggers for python-support ... 
Setting up linux-image-2.6.38-10-generic (2.6.38-10.46) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic 
 * dkms: running auto installation service for kernel 2.6.38-10-generic 
 
 *       nvidia-173 (173.14.30)... 
   ...fail! 
 *       virtualbox-ose (4.0.4)... 
   ...fail! 
 *       nvidia-current (270.41.06)... 
   ...fail! 
dkms: WARNING: linux headers are missing, which may explain the above failures. 
      please install the linux-headers-2.6.38-10-generic package to fix this. 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic 
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic 
/usr/sbin/grub-probe: error: /boot/grub/device.map:3: No open parenthesis found. 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst line 1010. 
dpkg: error processing linux-image-2.6.38-10-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up lshw-gtk (02.15-1) ... 
Errors were encountered while processing: 
 linux-image-2.6.38-10-generic 
Setting up linux-image-2.6.38-10-generic (2.6.38-10.46) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic 
 * dkms: running auto installation service for kernel 2.6.38-10-generic 
 
 *       nvidia-173 (173.14.30)... 
   ...fail! 
 *       virtualbox-ose (4.0.4)... 
   ...fail! 
 *       nvidia-current (270.41.06)... 
   ...fail! 
dkms: WARNING: linux headers are missing, which may explain the above failures. 
      please install the linux-headers-2.6.38-10-generic package to fix this. 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic 
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic 
/usr/sbin/grub-probe: error: /boot/grub/device.map:3: No open parenthesis found. 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst line 1010. 
dpkg: error processing linux-image-2.6.38-10-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2

---

### Post by snowpine on 2011-07-17
I think the error is pretty self-explanatory:

> please install the linux-headers-2.6.38-10-generic package to fix this

so:

```
sudo apt-get install linux-headers-2.6.38-10-generic
```

---

### Post by daftlad on 2011-07-17
Tried that and I get 
sudo apt-get install linux-headers-2.6.38-10-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.38-10-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.38-10-generic (2.6.38-10.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
 * dkms: running auto installation service for kernel 2.6.38-10-generic         
 *       nvidia-173 (173.14.30)...                                       [ OK ] 
 *       virtualbox-ose (4.0.4)...                                       [ OK ] 
 *       nvidia-current (270.41.06)...                                   [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
/usr/sbin/grub-probe: error: /boot/grub/device.map:3: No open parenthesis found.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.38-10-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by terrykiwi83 on 2011-07-17
There is a program called **kernelcheck** it will download and install the latest kernel from kernel.org - I think its 2.6.39.3 at the moment. This done the trick for me.

Link: [http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)

---

