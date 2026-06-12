---
title: "Linux 2.6.35.25 kernel update failed"
date: 2011-01-14
forum: General Help
---

### Post by lbarnes on 2011-01-14
Ubuntu 10.10 64

My update failed today with the latest kernel release. It was about 6-9 updates all having to do with this kernel. I updated in Update Manager and can't seem to find a history/log to show you guys. This is my sudo apt-get dist-ugrade output:
```
lennon@lennon-HP-HDX-16-Notebook-PC:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.35-25-generic (2.6.35-25.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
 * dkms: running auto installation service for kernel 2.6.35-25-generic                                                                                                                          
 *       nvidia-current (260.19.29)...                                                                                                                                                    [ OK ] 
 *       ipheth (1.0)...                                                                                                                                                                  [ OK ] 
 *       vboxhost (4.0.0)...                                                                                                                                                              [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
/etc/default/grub: 23: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-25-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-25-generic; however:
  Package linux-image-2.6.35-25-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.35-25-generic
 linux-image-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
lennon@lennon-HP-HDX-16-Notebook-PC:~$ 

```
I also get this error message with sudo apt-get update but don't know where to start.
```
Reading package lists... Done
W: GPG error: http://www.sourceslist.eu maverick Release: The following signatures were invalid: BADSIG 536D7B78FA088BA5 Alessandro Lanave (repository gestito da Ingalex relativo al sito http://www.sourceslist.eu) <allanav@tin.it>
lennon@lennon-HP-HDX-16-Notebook-PC:~$ 

```
Any suggestions would be great, error messages simply drive crazy, thanks guys.

---

### Post by lbarnes on 2011-01-14
Solved by uncommenting line 23 in /etc/default/grub.
Repo error is no longer present.

---

