---
title: "kernal update problem"
date: 2011-07-17
forum: General Help
---

### Post by miko5054 on 2011-07-17
im trying to upgrade the kernal
```
 Setting up linux-image-2.6.38-10-generic (2.6.38-10.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
 * dkms: running auto installation service for kernel 2.6.38-10-generic         
 *       virtualbox-ose (4.0.4)...                                       [ OK ] 
 *       bcmwl (5.100.82.38+bdcom)...                                    [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
/etc/default/grub: 9: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-10-generic; however:
  Package linux-image-2.6.38-10-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.10.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.38-10-generic
 linux-image-generic
 linux-generic

```


any sugestions ?

---

### Post by miko5054 on 2011-07-17
this was the most importent line 
```
 /etc/default/grub: 9: splash: not found
```

replace this "  with '   
to solve it

---

### Post by tredegar on 2011-07-17
Perhaps tell us your current kernel version (and ubuntu distribution) and the command you gave to update your kernel?

---

