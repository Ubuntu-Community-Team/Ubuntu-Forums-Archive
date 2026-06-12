---
title: "apt-get install chokes on configuring linux-image-3.0.0-13-generic"
date: 2011-12-08
forum: General Help
---

### Post by molipha on 2011-12-08
Hi,

I'm assuming that running ubuntu from a pen drive is causing the error pasted below. I get it whether I'm running 32 or 64 bit. Is there any way to stop apt-get from trying to do this task? It takes a long time and runs every time I use apt-get to install something else.

Many thanks.


ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-image-3.0.0-13-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-3.0.0-13-generic (3.0.0-13.22) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
update-initramfs: Generating /boot/initrd.img-3.0.0-13-generic
cryptsetup: WARNING: failed to detect canonical device of overlayfs
cryptsetup: WARNING: could not determine root device from /etc/fstab
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.0.0-13-generic /boot/vmlinuz-3.0.0-13-generic
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.0.0-13-generic.postinst line 1010.
dpkg: error processing linux-image-3.0.0-13-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.0.0-13-generic; however:
  Package linux-image-3.0.0-13-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.0.0.13.15); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.0.0-13-generic
 linux-image-generic
 linux-generic

---

### Post by jerrrys on 2011-12-10
found this

[http://ubuntuforums.org/showthread.php?p=11518055#post11518055](http://ubuntuforums.org/showthread.php?p=11518055#post11518055)

---

