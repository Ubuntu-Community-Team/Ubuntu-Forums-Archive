---
title: "No matter what I install, I get an error - yet it works."
date: 2010-07-06
forum: General Help
---

### Post by Roasted on 2010-07-06
Whenever I install something from the software center, I get this error:


installArchives() failed: Selecting previously deselected package lsdvd.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 228774 files and directories currently installed.)
Unpacking lsdvd (from .../lsdvd_0.16-3ubuntu1_amd64.deb) ...
Selecting previously deselected package libopenal1.
Unpacking libopenal1 (from .../libopenal1_1%3a1.12.854-0ubuntu1~lucid1_amd64.deb) ...
Selecting previously deselected package libsvga1.
Unpacking libsvga1 (from .../libsvga1_1%3a1.4.3-29_amd64.deb) ...
Selecting previously deselected package mplayer.
Unpacking mplayer (from .../mplayer_2%3a1.0~rc3+svn20090426-1ubuntu16+medibuntu1_amd64.deb) ...
Selecting previously deselected package mencoder.
Unpacking mencoder (from .../mencoder_2%3a1.0~rc3+svn20090426-1ubuntu16+medibuntu1_amd64.deb) ...
Selecting previously deselected package acidrip.
Unpacking acidrip (from .../acidrip_0.14-0.2ubuntu5_all.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for menu ...
Processing triggers for python-support ...
Setting up linux-image-2.6.32-23-generic (2.6.32-23.37) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-23-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-23-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-23-generic; however:
  Package linux-image-2.6.32-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.23.24); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.32-23-generic (2.6.32-23.37) ...
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-23-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-23-generic; however:
  Package linux-headers-2.6.32-23-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Setting up lsdvd (0.16-3ubuntu1) ...
No apport report written because MaxReports is reached already
Setting up libopenal1 (1:1.12.854-0ubuntu1~lucid1) ...

Setting up libsvga1 (1:1.4.3-29) ...

Setting up mplayer (2:1.0~rc3+svn20090426-1ubuntu16+medibuntu1) ...

Setting up mencoder (2:1.0~rc3+svn20090426-1ubuntu16+medibuntu1) ...
Setting up acidrip (0.14-0.2ubuntu5) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 linux-image-2.6.32-23-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.32-23-generic
 linux-headers-generic
Setting up linux-headers-2.6.32-23-generic (2.6.32-23.37) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-23-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.32-23-generic (2.6.32-23.37) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-23-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-23-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-23-generic; however:
  Package linux-image-2.6.32-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.23.24); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-23-generic; however:
  Package linux-headers-2.6.32-23-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured


However, the package itself succeeds with installation. Looks to me like it's a problem with a kernel I installed. How can I fix?

---

### Post by philinux on 2010-07-06
See what this spits out.

```
sudo dpkg --configure -a
```

---

### Post by Roasted on 2010-07-06
jason@Area51:~$ sudo dpkg --configure -a
[sudo] password for jason: 
Setting up linux-headers-2.6.32-23-generic (2.6.32-23.37) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-23-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.32-23-generic (2.6.32-23.37) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-23-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-22-generic
Found initrd image: /boot/initrd.img-2.6.32-22-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda1
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.32-23-generic /boot/vmlinuz-2.6.32-23-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.32-23-generic.postinst line 1003.
dpkg: error processing linux-image-2.6.32-23-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-23-generic; however:
  Package linux-image-2.6.32-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.23.24); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-23-generic; however:
  Package linux-headers-2.6.32-23-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.32-23-generic
 linux-image-2.6.32-23-generic
 linux-image-generic
 linux-generic
 linux-headers-generic
jason@Area51:~$

---

### Post by IzByFl on 2010-07-07
same problem here, and "sudo dpkg --configure -a" doesn't help!

---

### Post by IzByFl on 2010-07-07
i found this
[http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/](http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/)

post #6 worked for me

---

