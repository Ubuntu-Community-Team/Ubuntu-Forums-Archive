---
title: "dpkg proplems please help!"
date: 2010-11-24
forum: General Help
---

### Post by nolag on 2010-11-24
When I try to install anything I get the following error:

Sub-process /usr/bin/dpkg returned an error code (1)

I don't know what else I can say to give more info that can help.

---

### Post by wilee-nilee on 2010-11-24
> **nolag said:**
> When I try to install anything I get the following error:

Sub-process /usr/bin/dpkg returned an error code (1)

I don't know what else I can say to give more info that can help.

Try running these two commands, in a terminal. Make sure nothing is open but the terminal.
sudo dpkg --configure -a
sudo apt-get install -f

---

### Post by nolag on 2010-11-24
Thanks my output is attached, it had errors :(

---

### Post by wilee-nilee on 2010-11-24
> **nolag said:**
> Thanks my output is attached, it had errors :(

Well I am not a log reader but post the whole shebang including the command.

---

### Post by nolag on 2010-11-24
Sure, the text file was that but here
 
 
sudo dpkg --configure -a
Setting up linux-headers-2.6.35-23-generic (2.6.35-23.40) ...
Setting up linux-image-2.6.35-23-generic (2.6.35-23.40) ...
g /etc/kernel/header_postinst.d/dkms 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
* dkms: running auto installation service for kernel 2.6.35-23-generic
 
* fglrx (8.780)...
...done.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.35-23-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.35-23-generic (--configure):
subprocess installed post-installation script returned error exit status 2
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-23-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
* dkms: running auto installation service for kernel 2.6.35-23-generic
 
* fglrx (8.780)...
...done.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-23-generic /boot/vmlinuz-2.6.35-23-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-23-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-23-generic (--configure):
subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
linux-image-generic depends on linux-image-2.6.35-23-generic; however:
Package linux-image-2.6.35-23-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
linux-generic depends on linux-image-generic (= 2.6.35.23.25); however:
Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
linux-headers-generic depends on linux-headers-2.6.35-23-generic; however:
Package linux-headers-2.6.35-23-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
dependency problems - leaving unconfigured
Errors were encountered while processing:
linux-headers-2.6.35-23-generic
linux-image-2.6.35-23-generic
linux-image-generic
linux-generic
linux-headers-generic
 
sudo apt-get install -f
Setting up linux-headers-2.6.35-23-generic (2.6.35-23.40) ...
Setting up linux-image-2.6.35-23-generic (2.6.35-23.40) ...

---

### Post by wilee-nilee on 2010-11-24
Hopefully that will make sense to someone, did you try the second command?

---

### Post by nolag on 2010-11-25
> **wilee-nilee said:**
> Hopefully that will make sense to someone, did you try the second command?
 
Yes, it is at the end of what I said.  I will edit my post and put a line break so it is more visible.  I am thinking of reformating the ubuntu partition, the problem seems to be with the kernel :(.

---

