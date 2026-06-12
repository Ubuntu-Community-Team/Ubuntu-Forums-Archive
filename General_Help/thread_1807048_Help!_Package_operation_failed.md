---
title: "Help! Package operation failed"
date: 2011-07-18
forum: General Help
---

### Post by zteel on 2011-07-18
hi every one 
I'm having problem every time i install or uninstall something and then the icon to shut down the computer turns red and i need  to restart to complete update

Package operation failed
The installation or removal of a software package failed.
> installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 244413 files and directories currently installed.) 
Removing springlobby ... 
Processing triggers for hicolor-icon-theme ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Can't open /usr/share/applications/avast.desktop: No such file or directory at -e line 1, <> line 110. 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for man-db ... 
Processing triggers for python-support ... 
Setting up linux-image-2.6.39-02063901-generic (2.6.39-02063901.201106030905) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.39-02063901-generic 
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8105e-1.fw for module r8169 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.39-02063901-generic /boot/vmlinuz-2.6.39-02063901-generic 
 * dkms: running auto installation service for kernel 2.6.39-02063901-generic 
 
 *       virtualbox-ose (4.0.4)... 
   ...done. 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.39-02063901-generic /boot/vmlinuz-2.6.39-02063901-generic 
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.39-02063901-generic /boot/vmlinuz-2.6.39-02063901-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.39-02063901-generic /boot/vmlinuz-2.6.39-02063901-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.39-02063901-generic /boot/vmlinuz-2.6.39-02063901-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.39-02063901-generic /boot/vmlinuz-2.6.39-02063901-generic 
/etc/default/grub: 11: splash: not found 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.39-02063901-generic.postinst line 1010. 
dpkg: error processing linux-image-2.6.39-02063901-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 linux-image-2.6.39-02063901-generic 
Setting up linux-image-2.6.39-02063901-generic (2.6.39-02063901.201106030905) ... 
Running depmod. 
update-initramfs: Generating /boot/initrd.img-2.6.39-02063901-generic 
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8105e-1.fw for module r8169 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.39-02063901-generic /boot/vmlinuz-2.6.39-02063901-generic 
 * dkms: running auto installation service for kernel 2.6.39-02063901-generic 
 
 *       virtualbox-ose (4.0.4)... 
   ...done. 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.39-02063901-generic /boot/vmlinuz-2.6.39-02063901-generic 
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.39-02063901-generic /boot/vmlinuz-2.6.39-02063901-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.39-02063901-generic /boot/vmlinuz-2.6.39-02063901-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.39-02063901-generic /boot/vmlinuz-2.6.39-02063901-generic 
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.39-02063901-generic /boot/vmlinuz-2.6.39-02063901-generic 
/etc/default/grub: 11: splash: not found 
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.39-02063901-generic.postinst line 1010. 
dpkg: error processing linux-image-2.6.39-02063901-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2
i thing the problem is the kernel 2.6.39 but i don't know how to fix it
i goolged my problem and i found [http://ubuntuforums.org/showthread.php?t=1477604](http://ubuntuforums.org/showthread.php?t=1477604) but it didn't  help but i used this command 
sudo dpkg --configure -a
and here is the reply
> zteel@EBANO:~$ sudo dpkg --configure -a
[sudo] password for zteel: 
Setting up linux-image-2.6.39-02063901-generic (2.6.39-02063901.201106030905) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.39-02063901-generic
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8105e-1.fw for module r8169
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.39-02063901-generic /boot/vmlinuz-2.6.39-02063901-generic
 * dkms: running auto installation service for kernel 2.6.39-02063901-generic                                                                                   
 *       virtualbox-ose (4.0.4)...                                       [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.39-02063901-generic /boot/vmlinuz-2.6.39-02063901-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.39-02063901-generic /boot/vmlinuz-2.6.39-02063901-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.39-02063901-generic /boot/vmlinuz-2.6.39-02063901-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.39-02063901-generic /boot/vmlinuz-2.6.39-02063901-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.39-02063901-generic /boot/vmlinuz-2.6.39-02063901-generic
/etc/default/grub: 11: splash”: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.39-02063901-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.39-02063901-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.39-02063901-generic


---

### Post by Frogs Hair on 2011-07-18
What version of Ubuntu ? I receive proposed updates for 11.04 and don't have the 2.6.39  kernel yet .

It possible to install that kernel on 11.04 with a PPA . If your are testing 11.10 there is a thread dedicated to it . [http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0](http://ubuntuguide.net/ubuntu-11-04-upgrade-linux-kernel-to-2-6-39-0)

---

### Post by zteel on 2011-07-18
im using ubuntu 11.04
and I up date the kernel with a guide

---

### Post by Frogs Hair on 2011-07-18
The link I added suggested to check for 11.04 PPA packages at one of links included on the page and there are none .

Another link leads to the kernel package , but with no guide . The following line appears in both terminal outputs and may be your problem . If you don't have a specific need for this kernel it may not be worth the trouble.     ```
W: Possible missing firmware /lib/firmware/rtl_nic/rtl8105e-1.fw for module r8169 
 Examining /etc/kernel/postinst.d.
```

If you manage to get it installed remember to watch the update manager or turn off kernel updates in synaptic . You will receive updates for the old kernel and it will downgrade your kernel if you install those updates.

---

### Post by ajgreeny on 2011-07-18
> **zteel said:**
> im using ubuntu 11.04
and I up date the kernel with a guide
What guide?  It must be from some organisation that does not follow standard guidelines, I think.

---

