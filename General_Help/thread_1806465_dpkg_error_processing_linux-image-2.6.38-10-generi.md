---
title: "dpkg: error processing linux-image-2.6.38-10-generic"
date: 2011-07-17
forum: General Help
---

### Post by Dr Zin on 2011-07-17
I had a bad connection when I got the upgrade notice for this kernel.  It broke on and I have tried to go into recovery mode. That failed I removed it and I have tried purging it, but nothing has work so far.

```
sudo apt-get autoremove
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-2.6.38-10-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 148 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 173052 files and directories currently installed.)
Removing linux-image-2.6.38-10-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/README: 2: All: not found
/etc/grub.d/README: 4: 00_*:: not found
/etc/grub.d/README: 5: 10_*:: not found
/etc/grub.d/README: 6: Syntax error: "(" unexpected
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postrm line 328.
dpkg: error processing linux-image-2.6.38-10-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.38-10-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```



Does any one have any ideas to get this working again?

---

### Post by Dr Zin on 2011-07-18
additional code```
 sudo apt-get install linux-image-2.6.38-10-generic
[sudo] password for drzin: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-2.6.38-10-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.38-10-generic (2.6.38-10.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
 * dkms: running auto installation service for kernel 2.6.38-10-generic         
 *       vboxhost (4.0.12)...                                            [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/README: 2: All: not found
/etc/grub.d/README: 4: 00_*:: not found
/etc/grub.d/README: 5: 10_*:: not found
/etc/grub.d/README: 6: Syntax error: "(" unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.38-10-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by zealibib slaughter on 2011-07-18
try 
dpkg --configure -a
apt-get -f install

---

### Post by Dr Zin on 2011-07-19
So, here are my results


```
root@localhost:/home/me# dpkg --configure -a
Setting up linux-image-2.6.38-10-generic (2.6.38-10.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
 * dkms: running auto installation service for kernel 2.6.38-10-generic         
 *       vboxhost (4.0.12)...                                            [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/README: 2: All: not found
/etc/grub.d/README: 4: 00_*:: not found
/etc/grub.d/README: 5: 10_*:: not found
/etc/grub.d/README: 6: Syntax error: "(" unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.38-10-generic
root@localhost:/home/me# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-2.6.38-10-generic (2.6.38-10.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
 * dkms: running auto installation service for kernel 2.6.38-10-generic         
 *       vboxhost (4.0.12)...                                            [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.38-10-generic
Found initrd image: /boot/initrd.img-2.6.38-10-generic
Found linux image: /boot/vmlinuz-2.6.38-8-generic
Found initrd image: /boot/initrd.img-2.6.38-8-generic
Found memtest86+ image: /boot/memtest86+.bin
/etc/grub.d/README: 2: All: not found
/etc/grub.d/README: 4: 00_*:: not found
/etc/grub.d/README: 5: 10_*:: not found
/etc/grub.d/README: 6: Syntax error: "(" unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.38-10-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```



So, Tried to couple of other things.  Like, tried each of the packages and the same results. 

I think a base re-install I can't I have access to enough space, to back thing up.

FYI

It was giving  this before in stalled Virtualbox.

---

### Post by TimRiker on 2011-07-20
It looks like /etc/grub.d/README is trying to get executed.

Check the permissions on that file. They should be 644.

Try moving it someplace else, then installing your package.

Try reinstalling grub-pc and see if that fixes it.

---

### Post by Dr Zin on 2011-07-20
It seems to be working at this time.  I will keep open until I have fully tested it.   Thanks, Tim

---

