---
title: "Something's Wrong with Upgrading the the Latest Linux Kernel"
date: 2012-01-27
forum: General Help
---

### Post by Mars11 on 2012-01-27
This is what I get when trying to update, or install anything. ```
mars11@Arthur-Laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-3.0.0-15-generic (3.0.0-15.26) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
cp: cannot stat `/boot/initrd.img-3.0.0-15-generic': No such file or directory
Failed to copy /boot/initrd.img-3.0.0-15-generic to /initrd.img .
dpkg: error processing linux-image-3.0.0-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-15-generic; however:
  Package linux-image-3.0.0-15-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 3.0.0.15.17); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux:
 linux depends on linux-image (= 3.0.0.15.17); however:
  Package linux-image is not configured yet.
dpkg: error processing linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.0.0.15.17); however:
  Package linux-image-generic is nNo apport report written because the error message indicates its a followup error from a previous failure.
                                                            No apport report written because the error message indicates its a followup error from a previous failure.
      No apport report written because MaxReports is reached already
                                                                    No apport report written because MaxReports is reached already
                                                  ot configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.0.0-15-generic
 linux-image-generic
 linux-image
 linux
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by gregaryh on 2012-02-07
I am having the exact same issue. I am running Oneiric 64bit on a Lenovo Thinkpad W510. When I try removing the linux-generic package from within synaptic I get the following: 

(Reading database ... 230548 files and directories currently installed.)
Removing linux-image-3.0.0-15-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
dkms: removing: nvidia-current 280.13 (3.0.0-15-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  nvidia-current
Version: 280.13
Kernel:  3.0.0-15-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia_current.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.0.0-15-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall Completed.
dkms: removing: nvidia-current-updates 280.13 (3.0.0-15-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  nvidia-current-updates
Version: 280.13
Kernel:  3.0.0-15-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia_current_updates.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.0.0-15-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall Completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
update-initramfs: Deleting /boot/initrd.img-3.0.0-15-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
/etc/default/grub: 36: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.0.0-15-generic.postrm line 328.
dpkg: error processing linux-image-3.0.0-15-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.0.0-15-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

### Post by gregaryh on 2012-02-21
So Now that the new 3.0.0.16 Kernel is out, I thought maybe I could upgrade to this, but it still fails. Here is the output from synaptic: 
```

Selecting previously deselected package linux-image-3.0.0-16-generic.
(Reading database ... 251952 files and directories currently installed.)
Unpacking linux-image-3.0.0-16-generic (from .../linux-image-3.0.0-16-generic_3.0.0-16.28_amd64.deb) ...
Done.
Selecting previously deselected package linux-image-generic.
Unpacking linux-image-generic (from .../linux-image-generic_3.0.0.16.19_amd64.deb) ...
Selecting previously deselected package linux-image.
Unpacking linux-image (from .../linux-image_3.0.0.16.19_amd64.deb) ...
Setting up linux-image-3.0.0-15-generic (3.0.0-15.26) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
/etc/default/grub: 36: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-15-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-3.0.0-16-generic (3.0.0-16.28) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
/etc/default/grub: 36: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-16-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-16-generic; however:
  Package linux-image-3.0.0-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 3.0.0.16.19); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.0.0-15-generic
 linux-image-3.0.0-16-generic
 linux-image-generic
 linux-image
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-3.0.0-15-generic (3.0.0-15.26) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
/etc/default/grub: 36: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-15-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.0.0-16-generic (3.0.0-16.28) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
/etc/default/grub: 36: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-16-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-16-generic; however:
  Package linux-image-3.0.0-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 3.0.0.16.19); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.0.0-15-generic
 linux-image-3.0.0-16-generic
 linux-image-generic
 linux-image

```

When I try to remove the offending package, it fails as well. I have tried a complete removal, and a re-install. Here is what that produces:
```
(Reading database ... 255922 files and directories currently installed.)
Removing linux-image-3.0.0-15-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
dkms: removing: nvidia-current 280.13 (3.0.0-15-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  nvidia-current
Version: 280.13
Kernel:  3.0.0-15-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia_current.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.0.0-15-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall Completed.
dkms: removing: nvidia-current-updates 280.13 (3.0.0-15-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  nvidia-current-updates
Version: 280.13
Kernel:  3.0.0-15-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia_current_updates.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.0.0-15-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall Completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
update-initramfs: Deleting /boot/initrd.img-3.0.0-15-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-15-generic /boot/vmlinuz-3.0.0-15-generic
/etc/default/grub: 36: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.0.0-15-generic.postrm line 328.
dpkg: error processing linux-image-3.0.0-15-generic (--purge):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.0.0-15-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-3.0.0-16-generic (3.0.0-16.28) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-16-generic /boot/vmlinuz-3.0.0-16-generic
/etc/default/grub: 36: Syntax error: EOF in backquote substitution
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-16-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-16-generic; however:
  Package linux-image-3.0.0-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 3.0.0.16.19); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.0.0-16-generic
 linux-image-generic
 linux-image


```

I have also tried running apt-get autoclean which runs successfully, but doesn't seem to change anything.

Anyone have any other ideas?

---

### Post by Morozov on 2012-02-21
Guys, wait for 12.04 hope it should be soon avaliable. I did kernel upgrade on Dell Studio xps 1340 with one problem wireless was not recognized so had to find way arround, any way (computer handled much better, run "coller" (know issues with Nvidia card) as well) but then I try 12.04 with 3.2 kernel. Tell you one thing this is my next OS
Regards

---

